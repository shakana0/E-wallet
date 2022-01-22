<template >
  <div class="register-wrapper">
    <form @keyup="submitCardInfo">
      <label for="CARD NUMBER">CARD NUMBER</label>
      <input
        type="number"
        placeholder="Card Number"
        v-model.number="cardInfo.cardNumber"
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
            <option value="" v-for="n in 12" :key="n">
              {{ n }}
            </option>
          </select>
        </div>

        <div>
          <label for="Year">Year</label>
          <select name="dropdown" id="" v-model="cardInfo.expireYear">
            <option value="" v-for="n in 5" :key="n">
              {{ n + 21 }}
            </option>
          </select>
        </div>
      </section>

      <label for="CCV">CCV</label>
      <input type="text" placeholder="CCV" v-model="cardInfo.CCV" />
      <label for="VENDOR">VENDOR</label>
      <!-- <select name="dropdown" id="" v-model="cardInfo.vendor"></select> -->
      <select name="dropdown" id="">
        <option value="">Bitcoin Inc</option>
        <option value="">Blockchain Inc</option>
        <option value="">Evil Corp</option>
        <option value="">Ninja Bank</option>
      </select>

      <button @submit.prevent="$emit('submitCard', cardInfo)">Add Card</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardInfo: {
        cardNumber: "",
        cardHolder: "",
        expireMonth: "",
        expireYear: "",
        CCV: "",
        vendor: "",
      },
    };
  },
  methods: {
    submitCardInfo() {
      this.$emit("send", { ...this.cardInfo });
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