<template>
  <div class="upgrades">
    <div v-for="(upgrade, index) in upgrades" :key="index" class="upgrade">
      <button
        @click="()=>{
        buyUpgrade(index)
        }"
        :class="`button ${upgrade.disabled ? 'disabled' : ''} `"
      >{{ upgrade.name }} {{ upgrade.disabled ? `(lvl: ${upgrade.unlocksAt})` : ''}}</button>

      <div class="details">
        <div class="cost">Cost: {{ upgrade.cost }}</div>
        <div class="quantity">Quantity: {{ upgrade.quantity }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "upgrades",
  computed: {
    upgrades() {
      return this.$store.getters.availableUpgrades;
    }
  },
  methods: {
    buyUpgrade(index) {
      this.$store.commit("buyUpgrade", {
        index,
        amount: 1
      });
    }
  }
};
</script>

<style lang="scss">
.upgrades {
  background-color: #222;
  padding: 25px;
  .upgrade {
    display: flex !important;
    justify-content: center !important;
    align-items: center !important;
    margin: 0px -15px 15px;
    .button,
    .cost,
    .quantity {
      color: #fff;
      margin: 0 15px;
    }

    // .details {
    //   flex: 1 1 100%;
    // }

    .button {
      appearance: none;
      border: none;
      outline: none;
      background: none;

      display: inline-block;
      min-width: 35%;
      padding: 15px 25px;
      background-color: #28a484;

      color: #fff;
      font-size: 19px;
      font-weight: 695;
      text-align: center;
      text-transform: uppercase;

      cursor: pointer;

      &.disabled {
        color: #222;
        background-color: #ccc;
        pointer-events: none;
        // flex: 1 1 100%;
      }
    }
  }
}

@media screen and (max-width: 1199px) {
  .button {
    appearance: none;
    border: none;
    outline: none;
    background: none;

    display: inline-block;
    width: 45%;
    padding: 15px 25px;
    background-color: #28a484;

    color: #fff;
    font-size: 19px;
    font-weight: 695;
    text-align: center;
    text-transform: uppercase;

    cursor: pointer;

    &.disabled {
      color: #222;
      background-color: #ccc;
      pointer-events: none;
      // flex: 1 1 100%;
    }
  }
}
</style>