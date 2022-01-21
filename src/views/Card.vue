<template>
  <div class="card">
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

      <div>
        <p class="card-number">{{ cardInfo.cardNumber }}</p>
      </div>
      <p class="cardholder-name">{{ cardInfo.cardHolder }}</p>
      <p class="month">{{ cardInfo.expireMonth }}</p>
      <p class="year">{{ cardInfo.expireYear }}</p>
      <p class="ccv">{{ cardInfo.CCV }}</p>
      <!-- <p class="vendor"  v-for="item in cardInfo.vendor" :key="item">{{item}}</p> -->
    </article>

    <RegisterCard @send="register" />
  </div>
</template>

<script>
import RegisterCard from "../components/RegisterCard.vue";
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
      console.log(cardInfo);
    },
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
}
</style>