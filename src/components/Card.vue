<template>
  <div class="card">
    <h1>ADD A NEW CARD BANK</h1>

    <article  :class="color">
      <section class="top-logo">
        <div class="logo">
          <div>
            <img :src="wifi" alt="wifi-logo"  width="44" height="44"/>
          </div>
          <div>
            <img src="../assets/chip.svg" alt="chip-logo" />
          </div>
        </div>
        <div>
          <img  width="50" :src="logo" alt="vendor-logo" />
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
          <!-- <p>MM/YY</p> -->
          <p>{{ cardInfo.expireMonth }} / {{ cardInfo.expireYear }}</p>
        </div>
      </section>
      <p class="cvc">{{ cardInfo.CVC }}</p>
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
      color:"",
      logo: "",
      wifi: "",
      wifiArray: {
          regularWifi: '../assets/wifi_white.svg',
          whiteWifi: '../assets/wifi.svg'
        }
    };
  },
  methods: {
    register(cardInfo) {
      this.cardInfo = { ...cardInfo };
      this.selectVendor(cardInfo)
    },
    selectVendor(cardInfo){
      this.logo = require('../assets/' + cardInfo.vendor + '.svg') 
      this.wifi = require('../assets/' + 'wifi_white' + '.svg') 
      this.color = cardInfo.vendor
    },
  },
  beforeMount(){
      if(this.logo == '' && this.vendor == null){
        this.logo = require('../assets/bitcoin.svg')
        this.wifi = require('../assets/wifi.svg')
      }
  }
};
</script>

<style lang="scss" scoped>
.evil {
  background: linear-gradient(
      248.3deg,
      rgba(0, 0, 0, 0.16) 0%,
      rgba(0, 0, 0, 0) 100%
    ),
    #f33355;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
  p{
    color: white;
  }
}
.bitcoin {
  background: linear-gradient(
      248.04deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0) 99.07%
    ),
    #ffae34;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
}
.ninja {
  background: linear-gradient(
      248.3deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0) 100%
    ),
    #222222;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p{
    color: white;
  }
}
.blockchain {
  background: linear-gradient(
      248.52deg,
      rgba(0, 0, 0, 0.15) 1.49%,
      rgba(0, 0, 0, 0) 100%
    ),
    #8b58f9;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
    p{
    color: white;
  }
}
article {
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
      margin: 0;
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