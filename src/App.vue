<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" @click="change" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Demo :userName="userName" url="222"></Demo>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Demo from "./components/Demo.vue";
import { ref } from "vue";
export default {
  name: "App",
  components: {
    // HelloWorld,
    Demo
  },
  setup() {
    const userName = ref("firstnote");
    const change = () => {
      userName.value = "xiaoqiao";
    };
    return {
      userName,
      change
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
