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
      // console.log("It's working");
      this.$store.commit("incrementBytes", this.$store.state.bpk);
    },
    loop() {
      // GAME LOOP
      this.levelManager();
      requestAnimationFrame(this.loop);
    },
    levelManager() {
      console.log("FPS");
      if (this.$store.getters.bytesUntilLevelUp <= 0) {
        this.$store.commit("levelUp");
      }
    }
  },
  created() {
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
