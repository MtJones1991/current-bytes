<template>
  <div class="overview">
    <h3>Current Bytes</h3>
    <div class="bytes">{{ bytes }}</div>
    <div class="bps">Bytes per second {{ bps }}</div>
    <div class="level">Current level: {{ level }}</div>
    <div class="next-level">Bytes until next level: {{ bytesUntilLevelUp }}</div>
  </div>
</template>

<script>
export default {
  name: "overview",
  computed: {
    bytes() {
      return Math.round(this.$store.state.bytes);
    },
    bps() {
      return this.$store.state.bps.toFixed(1);
    },
    level() {
      return this.$store.state.player.level;
    },
    bytesUntilLevelUp() {
      return this.$store.getters.bytesUntilLevelUp;
    }
  }
};
</script>

<style lang="scss">
.overview {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px;
}

h3 {
  color: #222;
  font-size: 23px;
  font-weight: 395;
  margin-bottom: 15px;
}

.bytes {
  width: 100%;
  min-width: 195px;
  max-width: fit-content;
  padding: 15px 25px;
  background-color: #28a484;
  border-radius: 7px;

  color: #fff;
  font-size: 55px;
  font-weight: 895;
  text-align: center;
  margin-bottom: 29px;
}

.bps,
.level,
.next-level {
  margin-bottom: 15px;

  color: #222;
  font-size: 17px;
  font-weight: 495px;
  font-style: italic;
  text-align: center;
}
</style>