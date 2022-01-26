<template>
  <div>
    <RegisterCard @submitCard="submittedCard" @changePage="$emit('changePage')" />
  </div>
</template>

<script>
import RegisterCard from "../components/RegisterCard.vue";
export default {
  components: { RegisterCard },

  methods: {
    submittedCard(cardInfo) {
      this.$emit("submittedCard", cardInfo);
    },
  },
  getfun() {
    console.log("hejsan igen");
  },
};
</script>

<style lang="sass" scoped>
</style>