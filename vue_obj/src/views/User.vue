<template>
  <div class="user">
    <div class="inp">
      <p>
        <input
          type="text"
          placeholder="搜索歌曲、歌手、专辑"
          v-model="place"
          @input.enter="loaderinp"
        />
      </p>
    </div>
    <ul class="ullost">
      <li v-for="(rem, k) in relost" :key="k">{{ rem.first }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "User",
  data() {
    return {
      place: "",
      relost: [],
    };
  },
  methods: {
    // loaderinp() {
    // this.$http.get("/search/hot").then((data) => {
    // console.log(data);
    // this.relost = data.data.result;
    //   });
    // },
  },
  beforeRouteEnter(to, from, next) {
    next((vm) => {
      vm.$http.get("/search/hot").then((data) => {
        // console.log(data.data.result);
        vm.relost = data.data.result.hots;
      });
    });
  },
};
</script>
<style lang="less" scoped>
.user {
  .inp {
    width: 100%;
    height: 60px;
    background-color: #fbfcfd;
    input {
      width: 80%;
      height: 30px;
      line-height: 30px;
      border-radius: 30px;
      padding: 0 40px;
      outline: none;
      background: none;
      background-color: #ebecec;
      border: none;
      margin: 15px auto;
    }
  }
  ul.ullost {
    li {
      line-height: 30px;
      margin-left: 20px;
      float: left;
    }
  }
}
</style>