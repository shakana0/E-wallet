<template >
  <div class="register-wrapper" v-if="currentView == 'add-card'">
    <h1>ADD A NEW CARD BANK</h1>
    <Card :renderCard="cardInfo" />
    <div v-for="error in errors" :key="error">
      <h3>{{ error }}</h3>
    </div>
    <form @submit.prevent="formValidation">
      <label for="CARD NUMBER">CARD NUMBER</label>
      <input
        type="text"
        maxlength="16"
        placeholder="Card Number"
        v-model="cardInfo.cardNumber"
      />

      <label for="CARDHOLDER NAME">CARDHOLDER NAME</label>
      <input
        type="text"
        placeholder="Firstname Lastname"
        v-model="cardInfo.cardHolder"
      />

      <section class="valid-through">
        <div>
          <label for="Month">Month</label>
          <select name="dropdown" id="" v-model="cardInfo.expireMonth">
            <option v-for="n in 12" :key="n">
              {{ n }}
            </option>
          </select>
        </div>

        <div>
          <label for="Year">Year</label>
          <select name="dropdown" id="" v-model="cardInfo.expireYear">
            <option v-for="year in 5" :key="year">
              {{ year + 21 }}
            </option>
          </select>
        </div>
      </section>

      <label for="CVC">CVC</label>
      <input
        type="text"
        placeholder="CCV"
        v-model="cardInfo.CVC"
        maxlength="3"
      />
      <label for="VENDOR">VENDOR</label>

      <select name="dropdown" id="" v-model="cardInfo.vendor">
        <option v-for="vendor in vendorArray" :key="vendor" :value="vendor">
          {{ vendor }}
        </option>
      </select>
      <button>Add Card</button>
    </form>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: { Card },
  props: ["cardList"],
  data() {
    return {
      errors: [],
      currentView: "add-card",
      cardInfo: {
        cardNumber: "",
        cardHolder: "",
        expireMonth: "",
        expireYear: "",
        CVC: "",
        vendor: "",
      },
      vendorArray: ["bitcoin", "blockchain", "evil", "ninja"],
      validChar: [
        "a",
        "b",
        "c",
        "d",
        "e",
        "f",
        "g",
        "h",
        "i",
        "j",
        "k",
        "l",
        "m",
        "n",
        "o",
        "p",
        "q",
        "r",
        "s",
        "t",
        "u",
        "v",
        "w",
        "x",
        "y",
        "z",
        "å",
        "ä",
        "ö",
        " ",
      ],
      validNum: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"],
    };
  },
  methods: {
    submitCard() {
      this.$emit("submitCard", this.cardInfo);
      this.$emit("changePage");
    },
    formValidation() {
      this.errors = [];

      if (this.cardInfo.cardNumber === "") {
        this.errors.push("Card number required");
      }
       if (this.cardInfo.cardNumber.length < 16) {
        this.errors.push("Card number must contain 16 characters");
      }
      for (let i = 0; i < this.cardInfo.cardNumber.length; i++) {
        if (!this.validNum.includes(this.cardInfo.cardNumber[i])) {
          this.errors.push("Invalid character in chard number");
        }
      }

      if (this.cardInfo.cardHolder === "") {
        this.errors.push("Card holder name required");
      }
      for (let i = 0; i < this.cardInfo.cardHolder.length; i++) {
        if (!this.validChar.includes(this.cardInfo.cardHolder[i])) {
          this.errors.push("Invalid character in chard holder name");
        }
      }
      if (this.cardInfo.expireMonth === "") {
        this.errors.push("Month required");
      }
      if (this.cardInfo.expireYear === "") {
        this.errors.push("Year required");
      }
      if (this.cardInfo.CVC === "") {
        this.errors.push("CVC required");
      }
      if (this.cardInfo.vendor === "") {
        this.errors.push("Vendor required");
      }
      for (const card of this.cardList) {
        if (card.cardNumber == this.cardInfo.cardNumber) {
          this.errors.push("This card number already exists");
        }
      }
      if (!this.errors.length) {
        this.submitCard();
      }
    },
  },
};
</script>

<style lang="scss" scoped>
h3 {
  color: red;
}
.register-wrapper {
  h1 {
    margin-top: 5rem;
  }
  form {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;

    p {
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