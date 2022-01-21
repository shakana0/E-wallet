<template>
  <div id="app">
    <nav>
      <a @click="currentView = 'e-wallet'">E-wallet</a>
      <a @click="currentView = 'add-card'">Add Card</a>
    </nav>
    <Card v-if="currentView == 'add-card'" />
    <CardsInWallet v-else-if="currentView == 'e-wallet'" />
  </div>
</template>

<script>
import Card from "./views/Card.vue";
import CardsInWallet from "./views/CardsInWallet.vue";
export default {
  components: { Card, CardsInWallet },
  data() {
    return {
      currentView: "e-wallet",
    };
  },

};
</script>

<style  lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Red+Hat+Display:wght@400;800&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Red+Hat+Display:wght@800&display=swap");

$activeColor: rgba(235, 235, 235, 0.384);

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  h1 {
    font-family: "Red Hat Display", sans-serif;
    font-weight: 800;
     margin-top: 4rem;
  }
  p {
    font-family: "Red Hat Display", sans-serif;
  }
  nav {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    a {
      cursor: pointer;
      padding: 1rem;
      font-weight: 800;
      font-size: 1.2rem;

      &:hover {
        background-color: $activeColor;
      }
    }
  }
}
</style>