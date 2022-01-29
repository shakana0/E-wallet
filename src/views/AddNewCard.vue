<template>
  <div>
    <RegisterCard @submitCard="submittedCard" 
    @changePage="$emit('changePage')"
    :cardList="cardList"
     />
  </div>
</template>

<script>
import RegisterCard from "../components/RegisterCard.vue";
export default {
  components: { RegisterCard },
  props:['cardList'],

  methods: {
    submittedCard(cardInfo) {
      this.$emit("submittedCard", cardInfo);
    },
  },
};
</script>

<style lang="sass" scoped>
</style>