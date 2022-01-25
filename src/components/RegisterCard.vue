<template >
  <div class="register-wrapper"  v-if="currentView == 'add-card'">
        <h1>ADD A NEW CARD BANK</h1>

     <Card :renderCard="cardInfo"/>

    <form @submit.prevent="$emit('submitCard', cardInfo)">
      <label for="CARD NUMBER">CARD NUMBER</label>
      <input
        type="text"
        maxlength="19"
        placeholder="Card Number"
        v-model="cardInfo.cardNumber"
        @keyup="submitCardInfo"
      />

      <label for="CARDHOLDER NAME">CARDHOLDER NAME</label>
      <input
        type="text"
        maxlength="20"
        placeholder="Firstname Lastname"
        v-model="cardInfo.cardHolder"
        @keyup="submitCardInfo"
      />

      <section class="valid-through">
        <div>
          <label for="Month">Month</label>
          <select
            name="dropdown"
            id=""
            v-model="cardInfo.expireMonth"
            @change="submitCardInfo"
          >
            <option v-for="n in 12" :key="n">
              {{ n }}
            </option>
          </select>
        </div>

        <div>
          <label for="Year">Year</label>
          <select
            name="dropdown"
            id=""
            v-model="cardInfo.expireYear"
            @change="submitCardInfo"
          >
            <option v-for="year in 5" :key="year">
              {{ year + 21 }}
            </option>
          </select>
        </div>
      </section>

      <label for="CVC">CVC</label>
      <input type="text" placeholder="CCV" v-model="cardInfo.CVC" />
      <label for="VENDOR">VENDOR</label>

      <select
        name="dropdown"
        id=""
        v-model="cardInfo.vendor"
        @change="submitCardInfo"
      >
        <option v-for="vendor in vendorArray" :key="vendor" :value="vendor">
          {{vendor.split('').reverse().join('')}}
        </option>
      </select>

      <button @click="currentView === 'home'">Add Card</button>
    </form>
   
  </div>
</template>

<script>
import Card from './Card.vue'
export default {
  components: {Card},
  data() {
    return {
      currentView: 'add-card',
      cardInfo: {
        cardNumber: "",
        cardHolder: "",
        expireMonth: "",
        expireYear: "",
        CVC: "",
        vendor: "",
      },
      vendorArray: ["bitcoin", "blockchain", "evil", "ninja"],
    };
  },
  methods: {
    // FLYTTA TILL CARD!!!!!!!!!!!!!!!!!!!!
    submitCardInfo() {
        if (
          this.cardInfo.cardNumber.length === 4 ||
          this.cardInfo.cardNumber.length === 9 ||
          this.cardInfo.cardNumber.length === 14
        ) {
          this.cardInfo.cardNumber += " ";
          console.log("helloooo");
        }
        // this.emit('renderCard', this.cardInfo)
        this.$emit("send", this.cardInfo);
    },

  },
};
</script>

<style lang="scss" scoped>
.register-wrapper {
  h1 {
    margin-top: 4rem;
  }
  form {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;

    p{
      color: red;
    }

    input {
      padding: 9px 20px;
      border-radius: 5px;
      border: 1px solid black;
    }
    label {
      font-size: 0.8rem;
      margin: 0.8rem 0 0.2rem 0;
    }
    select {
      padding: 9px 40px;
      border-radius: 5px;
      border: 1px solid black;
    }
    .valid-through {
      display: flex;
      justify-content: space-between;

      div {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-content: center;

        label {
          font-size: 0.8rem;
        }

        select {
          padding: 9px 60px;
          border-radius: 5px;
          border: 1px solid black;
        }
      }
    }
  }
  button {
    margin-top: 2rem;
    padding: 0 75px;
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
}
</style>