<template>
  <div id="app">
    <Topnav></Topnav>
    <keep-alive>
      <router-view />
    </keep-alive>
  </div>
</template>
<script>
import Topnav from "./components/Topnav";
export default {
  name: "App",
  components: {
    Topnav,
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  display: flex;
  justify-content: space-between;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
