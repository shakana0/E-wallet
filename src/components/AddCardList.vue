<template>
    <div class="add-card-to-wallet">

        
   <Card @submitCard="addCardToList" />

    </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  components: { Card },
  data(){return{
      newCard: []
  }},
  methods:{
      addCardToList(cardInfo){
          this.newCard.push(cardInfo)
      }
  }
};
</script>