<template>
    <div class="add-card-to-wallet">

        
   <Card @addCard="addCardToList" />

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