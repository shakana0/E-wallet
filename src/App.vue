<template>
  <div id="app">
    <nav>
      <a @click="currentView = 'home'">E-wallet</a>
      <a @click="currentView = 'add-card'">Add Card</a>
    </nav>
    <AddNewCard
      v-if="currentView == 'add-card'"
      @submittedCard="addCardToList"
    />

    <Home v-else-if="currentView == 'home'" :cardArray="cardList"/>
  </div>
</template>

<script>
import AddNewCard from "./views/AddNewCard.vue";
import Home from "./views/Home.vue";
export default {
  components: { AddNewCard, Home },
  data() {
    return {
      currentView: "home",
      cardList: [],
    };
  },
  methods: {
    addCardToList(cardInfo) {
      this.cardList.push(cardInfo);
      console.log(this.cardList);
    },
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
    font-family: "PT Mono', monospace", sans-serif;
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