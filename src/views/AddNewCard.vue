<template>
    <div>

        <RegisterCard @submitCard="submittedCard"/>
    </div>
</template>

<script>
import RegisterCard from '../components/RegisterCard.vue'
export default {
    components:{RegisterCard},
    methods:{
submittedCard(cardInfo){
this.$emit('submittedCard', cardInfo)
}
    }
}
</script>

<style lang="sass" scoped>

</style>