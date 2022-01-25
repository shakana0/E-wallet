<template>
  <div class="home">
    <h1>E-WALLET</h1>

    <!-- <article class="active-card" v-if="cativeCard">
    </article> -->
    <div class="active-card">
      <Card :renderCard="kort" />
    </div>

    <div class="wallet-wrapper">
      <Card
        v-for="card in cardArray"
        :renderCard="card"
        :key="card.cardNumber"
        @active="renderActiveCard"
      />
    </div>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
export default {
  components: { Card },
  props: ["cardArray"],
  data() {
    return {
      kort: {},
    };
  },
  methods: {
    renderActiveCard(cardInfo) {
      this.kort = cardInfo;
      console.log(this.kort);
    },
  },
};
</script>

<style lang="scss" scoped>
h1 {
  text-align: center;
}
.wallet-wrapper {
  display: grid;
  grid-auto-rows: 4rem;
}
</style>
