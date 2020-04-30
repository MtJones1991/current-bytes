<template>
  <div id="game">
    <Overview />
    <router-view />
  </div>
</template>

<script>
import Overview from "./components/Overview";
export default {
  name: "app",
  components: {
    Overview
  },
  methods: {
    coding() {
      // DO SOMETHING
    },
    loop() {
      // GAME LOOP
      requestAnimationFrame(this.loop);
    }
  },
  cretaed() {
    this.loop();
    window.addEventListener("keypress", this.coding);
  },
  destroyed() {
    window.removeEventListener("keypress", this.coding);
  }
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}
</style>
