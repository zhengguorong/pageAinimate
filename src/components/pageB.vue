<template>
  <div>
    <div class="header">
      <div class="left" @click="goback"><</div>
      <div class="title">pageB</div>
    </div>
    <div>
    看到有很多小伙伴在大学期间做了各种有意义的事，比如旅行、做公益、写作，现在回想起来我的大学，让我最遗憾的不是谈了一场无疾而终的异地恋，也不是错过了数字可观的国家奖学金，而是说好的“等我上了大学，我要天天泡在图书馆里不能自拔，直至两耳不闻窗外事，一心只读圣贤书的境界”我没有达到。

2013年9月份正式参加工作，那时候我还在乡镇政府工作，没有万达广场、没有海底捞，下了班没有广场可逛，没有美食可享用，只好从当当上买来书，把它当精神食粮来啃。这一啃竟然上瘾了。

</div>
  </div>
</template>

<script>
export default {
  name: 'pageB',
  methods: {
    goback () {
      this.$router.goBack()
    }
  }
}
</script>

