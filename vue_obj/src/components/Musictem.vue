<template>
  <ul class="ulhost">
    <router-link tag="li" v-for="(rem, k) in removehost" :key="rem.id" to="/">
      <div class="top" v-if="kang" :class="{ con: k < 3 }">
        {{ (k + 1) | forNum }}
      </div>
      <div class="left">
        <div>{{ rem.name }}</div>
        <p>{{ rem.song.artists[0].name }}-{{ rem.name }}</p>
      </div>
      <div class="right"></div>
    </router-link>
  </ul>
</template>
<script>
export default {
  name: "Musictem",
  props: { removehost: Array, kang: Boolean },
  filters: {
    forNum(value) {
      if (value < 10) {
        value = "0" + value;
      }
      return value;
    },
  },
};
</script>
<style lang="less" scoped>
.ulhost {
  li {
    display: flex;
    margin: 10px 10px 0 10px;
    div.left {
      flex: 1;
      line-height: 25px;
      text-align: left;
      border-bottom: 1px solid #cccccc;
      div {
        font-size: 17px;
        color: #000;
      }
      p {
        font-size: 12px;
        color: #888;
        padding-left: 18px;
        position: relative;
      }
      p::after {
        content: "";
        position: absolute;
        top: 3px;
        left: -4px;
        width: 24px;
        height: 16px;
        background: url(../assets/Images/05.png) no-repeat 0px 0px;
        transform: scale(0.6);
      }
    }
    div.right {
      text-align: right;
      width: 45px;
      height: 44px;
      background: url(../assets/Images/05.png) no-repeat -47px 0px;
      transform: scale(0.5);
    }
    div.top {
      width: 40px;
      line-height: 50px;
      text-align: center;
    }
    div.con {
      color: red;
    }
  }
}
</style>