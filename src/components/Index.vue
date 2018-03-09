<template>
  <div>
    <div class="header">
      <div class="title">主页</div>
    </div>
     <ul>
        <li><router-link to="pageA">页面标题A</router-link></li>
        <li><router-link to="pageB">页面标题B</router-link></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'index'
}
</script>

<style>
  li {
    text-align: left;
  }
  a {
    text-decoration: none
    }
  a:active, a:active, a:visited {
    color: #000
  }
</style>

