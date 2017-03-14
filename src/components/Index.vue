<template>
  <div>
    <div class="header">
      <div class="title">主页</div>
    </div>
     <ul>
        <li><router-link to="pageA">pageA</router-link></li>
        <li><router-link to="pageB">pageB</router-link></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'index'
}
</script>
