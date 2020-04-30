<template>
  <div class="overview">
    <h3>Current Bytes</h3>
    <div class="bytes">{{ bytes }}</div>
    <div class="bps">Bytes per second {{ bps }}</div>
    <div class="level">Current level: {{ level }}</div>
    <div class="next-level">Bytes until next level: {{ bytesUntilNextLevel }}</div>
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
      return this.$store.state.level;
    },
    bytesUntilNextLevel() {
      return this.$store.getters.bytesUntilLevelUp;
    }
  }
};
</script>