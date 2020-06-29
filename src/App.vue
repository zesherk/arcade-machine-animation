<template>
  <div id="app">
    <ArcadeAnimation />
  </div>
</template>

<script>
import ArcadeAnimation from "./components/ArcadeAnimation.vue";

export default {
  name: "app",
  components: {
    ArcadeAnimation
  }
};
</script>

<style>
@import "./assets/css/main.css";
#app {
  height: 100%;
}
</style>
