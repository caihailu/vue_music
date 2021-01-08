<template>
  <h1 class="H1"><slot></slot></h1>
</template>
<script>
export default {};
</script>
<style lang="less" scoped>
.H1 {
  color: black;
  text-align: left;
  border-left: 2px solid red;
  padding-left: 10px;
  margin: 10px 0px;
}
</style>