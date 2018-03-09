<template>
  <div>
  <div class="header"></div>
  <transition :name="transitionName">
    <router-view class="child-view"></router-view>
  </transition>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        transitionName: 'slide-left'
      }
    },
    beforeRouteUpdate (to, from, next) {
      let isBack = this.$router.isBack
      if (isBack) {
        this.transitionName = 'slide-right'
      } else {
        this.transitionName = 'slide-left'
      }
      this.$router.isBack = false
      setTimeout(() => {
        next()
      }, 60)
    }
  }
</script>

<style scoped>
  .child-view {
    position: absolute;
    transition: all .4s cubic-bezier(.55,0,.1,1);
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: #fff;
  }
  .slide-left-enter, .slide-right-leave-active {
    -webkit-transform: translate(100%, 0);
    transform: translate(100%, 0);
    z-index: 1;
  }
  /* .slide-left-leave-active, .slide-right-enter {
    -webkit-transform: translate(-50px, 0);
    transform: translate(-50px, 0);
  } */
  .header {
    position:absolute;
    height:44px;
    width:100%
  }
</style>
