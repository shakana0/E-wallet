<template>
  <div class="card">
    <h1>ADD A NEW CARD BANK</h1>

    <article class="active-card">
      <section class="top-logo">
        <div class="logo">
          <div>
            <img src="../assets/wifi.svg" alt="wifi-logo" />
          </div>
          <div>
            <img src="../assets/chip.svg" alt="wifi-logo" />
          </div>
        </div>
        <div>
          <img
            class="card-logo"
            width="50"
            src="../assets/bitcoin.svg"
            alt="bitcoin-logo"
          />
        </div>
      </section>

      <div class="card-number">
        <p>{{ cardInfo.cardNumber }}</p>
      </div>
      <section class="bottom-section">
        <div>
          <p class="cardholder-name">Cardholder Name</p>
          <p>{{ cardInfo.cardHolder }}</p>
        </div>
        <div>
          <p class="valid-thru">Valid Thru</p>
          <p>MM/YY</p>
          <!-- <p> {{ cardInfo.expireMonth}} / {{cardInfo.expireYear }}</p> -->
        </div>
      </section>
      <p class="ccv">{{ cardInfo.CCV }}</p>
    </article>

    <RegisterCard @send="register" />
  </div>
</template>

<script>
import RegisterCard from "./RegisterCard.vue";
export default {
  components: { RegisterCard },
  data() {
    return {
      cardInfo: {},
    };
  },
  methods: {
    register(cardInfo) {
      this.cardInfo = { ...cardInfo };
      // console.log(cardInfo);
    },
    // submitCard(cardInfo) {
    //   this.$emit("addCardToList", cardInfo);
    // },
  },
};
</script>

<style lang="scss" scoped>
.active-card {
  width: 400px;
  height: 250px;
  background-color: rgba(235, 235, 235, 0.472);
  margin-top: 3rem;

  .top-logo {
    display: flex;
    justify-content: space-between;
    padding: 1rem 1rem 0 1rem;
  }
  p {
    padding: 0 1rem;
  }
  div p {
    padding: 0 1rem;
    margin-top: 1rem;
    font-weight: 800;
    font-size: 1.2rem;
  }
  div p:nth-child(2) {
    font-size: 0.9rem;
    font-weight: 600;
  }
  .card-number {
    height: 50px;
  }
  .bottom-section {
    display: flex;
    justify-content: space-between;

    p {
      font-size: 0.7rem;
      font-weight: normal;
    }
  }
}
button {
  margin-top: 2rem;
  padding: 0 10.5rem;
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