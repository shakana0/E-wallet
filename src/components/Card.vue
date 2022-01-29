<template>
  <div class="card">
    <article :class="renderCard.vendor"  @click="$emit('active', renderCard)">
      <section class="top-logo">
        <div class="logo">
          
            <img :src="wifiPath" alt="wifi-logo" width="44" height="44" />
         
          <div>
            <img src="../assets/chip.svg" alt="chip-logo" />
          </div>
        </div>
        <div>
          <img width="50" :src="logoPath" alt="vendor-logo" />
        </div>
      </section>

      <div class="card-number">
        <p>{{ checkCardNum }}</p>
      </div>
      <section class="bottom-section">
        <div>
          <p class="cardholder-name">Cardholder Name</p>
          <p>{{ renderCard.cardHolder }}</p>
        </div>
        <div>
          <p class="valid-thru">Valid Thru</p>
          <p>{{ renderCard.expireMonth }} / {{ renderCard.expireYear }}</p>
        </div>
      </section>
      <!-- <p class="cvc">{{ renderCard.CVC }}</p> -->
    </article>
  </div>
</template>

<script>
export default {
  props: ["renderCard"],
  computed: {
    logoPath() {
      if (!this.renderCard.vendor) {
        return require("../assets/bitcoin.svg");
      }
      return require("../assets/" + this.renderCard.vendor + ".svg");
    },

    wifiPath() {
      if (this.renderCard.vendor == "ninja") {
        return require("../assets/wifi_white.svg");
      }
      return require("../assets/wifi.svg");
    },
    checkCardNum() {
      let outPut = "";
      for (let i = 0; i < this.renderCard.cardNumber.length; i++) {
        outPut += this.renderCard.cardNumber[i];
        if ((i + 1) % 4 == 0) {
          outPut += " ";
        }
      }
      return outPut;
    },
  },
};
</script>

<style lang="scss" scoped>
.close {
  background-color: transparent;
  border: none;
}
.evil {
  background: linear-gradient(
      248.3deg,
      rgba(0, 0, 0, 0.16) 0%,
      rgba(0, 0, 0, 0) 100%
    ),
    #f33355;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
  p {
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
  p {
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
  p {
    color: white;
  }
}
article {
  width: 400px;
  height: 250px;
  background-color: rgba(235, 235, 235, 0.472);
  // margin-top: 3rem;

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
</style>