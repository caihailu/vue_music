<template>
  <div class="about">
    <div class="pmu">
      <img src="../assets/hot_music_bg_2x.jpg" alt="" />
      <div class="Hotsong">
        <p>更新日期∶01月07日</p>
      </div>
    </div>
    <Musictem :removehost="removehost" :kang="kang"></Musictem>
  </div>
</template>
<script>
import Musictem from "../components/Musictem";
export default {
  name: "About",
  data() {
    return { removehost: [], kang: true };
  },
  components: {
    Musictem,
  },
  beforeRouteEnter(to, from, next) {
    // console.log(1111111111);
    next((vm) => {
      vm.$http.get("/personalized/newsong").then((data) => {
        // console.log(data);
        vm.removehost = data.data.result;
      });
    });
  },
};
</script>
<style lang="less" scoped>
div.about {
  div.pmu {
    position: relative;
    img {
      vertical-align: middle;
    }
    div.Hotsong {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.3);
      padding: 25% 0 0 10%;
      box-shadow: border-box;
      p {
        text-align: left;
        font-size: 12px;
        color: #fff;
        position: relative;
      }
      p::after {
        content: "";
        position: absolute;
        top: -104px;
        left: -70px;
        width: 284px;
        height: 134px;
        background: url(../assets/Images/05.png) no-repeat -48px -59px;
        transform: scale(0.5);
      }
    }
  }
}
</style>
