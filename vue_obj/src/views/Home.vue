<template>
  <div class="home">
    <Title>推荐歌单</Title>
    <ul class="uls">
      <router-link tag="li" v-for="rem in removelist" :key="rem.id" to="/">
        <div class="relist">
          <img :src="rem.picUrl" alt="" />
          <p>{{ rem.name }}</p>
          <span>{{ rem.playCount | formatNum }}</span>
        </div>
      </router-link>
    </ul>
    <Title>最新音乐</Title>
    <Musictem :removehost="removehost" :kang="kang"></Musictem>
  </div>
</template>

<script>
import Title from "../components/Title";
import Musictem from "../components/Musictem";
export default {
  name: "Home",
  data() {
    return { removelist: [], removehost: [], kang: false };
  },
  components: {
    Title,
    Musictem,
  },
  filters: {
    formatNum(value) {
      return (value / 10000).toFixed(1) + "万";
    },
  },
  beforeRouteEnter(to, from, next) {
    next((vm) => {
      vm.$http.get("/personalized?limit=6").then((data) => {
        // console.log(data.data.result);
        vm.removelist = data.data.result;
      });
      vm.$http.get("/personalized/newsong").then((data) => {
        console.log(data.data.result);
        vm.removehost = data.data.result;
      });
    });
  },
};
</script>
<style lang="less" scoped>
ul.uls {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  li {
    width: 33%;
    div.relist {
      position: relative;
      margin-bottom: 15px;
      img {
        vertical-align: middle;
      }
      span {
        font-size: 12px;
        position: absolute;
        top: 2px;
        right: 3px;
        color: #fff;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
      }
      p {
        font-size: 14px;
        padding: 0 5px;
        line-height: 1.2;
        text-align: left;
        margin: 5px auto;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
      }
    }
  }
}
</style>
