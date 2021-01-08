<template>
  <ul class="topnav">
    <li><router-link to="/">推荐音乐</router-link></li>
    <li><router-link to="/about">热歌榜</router-link></li>
    <li><router-link to="/user">搜索</router-link></li>
  </ul>
</template>
<script>
export default {
  name: "Topnav",
};
</script>
<style lang="less" scoped>
.topnav {
  display: flex;
  border-bottom: #cccccc 1px solid;
  li {
    line-height: 40px;
    flex: 1;
    font-size: 15px;
    a {
      color: black;
      display: inline-block;
      text-decoration: none;
      &.router-link-exact-active {
        color: red;
        border-bottom: red 3px solid;
      }
    }
  }
}
</style>