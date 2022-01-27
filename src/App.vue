<template>
  <div id="app">
    <AddNewCard
      v-if="currentView == 'add-card'"
      @submittedCard="addCardToList"
      @changePage="homeView"
    />

    <Home
      v-else-if="currentView == 'home'"
      :cardArray="cardList"
      @changePage="addCardView"
    />
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
    addCardView() {
      this.currentView = "add-card";
    },
    addCardToList(cardInfo) {
      this.cardList.push(cardInfo);
      this.persist();
    },
    homeView() {
      this.currentView = "home";
    },

    persist() {
      localStorage.setItem("cards", JSON.stringify(this.cardList));
    },
  },

  beforeMount() {
    if (localStorage.getItem("cards"))
      this.cardList = JSON.parse(localStorage.getItem("cards"));
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
  padding: 0 2rem h1 {
    font-family: "Red Hat Display", sans-serif;
    font-weight: 800;
    margin-top: 4rem;
  }
  p {
    font-family: "PT Mono', monospace", sans-serif;
  }
}
</style>