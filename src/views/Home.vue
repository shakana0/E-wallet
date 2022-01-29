<template>
  <div class="home">
    <h1>E-WALLET</h1>
    <div class="active-card" v-if="showActive == true">
      <p>Active Card</p>
      <Card :renderCard="activeCard" />
      <button
        class="remove"
        @click="
          $emit('removeCard', activeCard),
            (activeCard = cardArray[cardArray.length - 1])
        "
      >
        Remove
      </button>
    </div>

    <div class="remove-dialog" v-if="showActive == true">
      <p>Are you sure you want to remove card?</p>
      <div>
        <button>Yes</button>
        <button>No</button>
      </div>
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
button.remove {
  background-color: rgb(248, 68, 68);
  color: white;
  padding: 0 50px;
  margin-left: 30%;
  margin-top: 3rem;
  box-shadow: 5px 3px 15px -3px #737373;

  &:hover {
    background-color: rgb(41, 40, 40);
  }
}

.remove-dialog {
  width: 300px;
  height: 200px;
  border: 2px solid black;
  box-shadow: 5px 3px 15px -3px #737373;
  background-color: white;
  // position: absolute;
  // top: 35%;
  // left: -70%
  div {
    margin: 4rem 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  button {
    padding: 0 20px;
    margin: 1rem;
    &:hover {
      background-color: red;
    }
  }
}
</style>
