<template>
  <div class="home">
    <h1>E-WALLET</h1>
    <div class="active-card" v-if="showActive == true">
      <p>Active Card</p>
      <Card :renderCard="activeCard" />
    </div>

    <div class="wallet-wrapper">
      <Card
        v-for="card in cardArray"
        :renderCard="card"
        :key="card.cardNumber"
        @active="renderActiveCard"
      />
    </div>
    <button @click="$emit('changePage')">Add New Card</button>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
export default {
  components: { Card },
  props: ["cardArray"],
  data() {
    return {
      activeCard: {},
      showActive: false,
    };
  },
  methods: {
    renderActiveCard(cardInfo) {
      this.activeCard = cardInfo;
      this.showActive = true;
    },
  },
};
</script>

<style lang="scss" scoped>
p {
  text-align: center;
  margin: 2rem 0 0 0;
  color: grey;
  font-size: 1rem;
}

h1 {
  text-align: center;
  margin-top: 5rem;
}
.wallet-wrapper {
  display: grid;
  grid-auto-rows: 4rem;
  margin-top: 3rem;
}
.active-card button {
  background-color: transparent;
  border: none;
  position: absolute;
  top: 33.5%;
  left: 22%;
  color: rgb(207, 2, 2);
  font-size: 2.5rem;
}
button {
  margin-top: 20rem;
  padding: 0 140px;
  color: white;
  background-color: black;
  font-size: 1rem;
  text-align: center;
  line-height: 2.5em;
  border-radius: 5px;

  &:hover {
    background-color: rgb(41, 40, 40);
  }
}
</style>
