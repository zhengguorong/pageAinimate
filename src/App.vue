<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
body {
  margin: 0 auto;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.header {
  width:100%;
  height:44px;
  background:#0058f1;
  color:#fff;
  line-height:44px;
  text-align: center;
}
.header .left {
  position: absolute;
  font-size: 20x;
  font-weight: bold;
  padding: 0px 20px;
}
</style>
