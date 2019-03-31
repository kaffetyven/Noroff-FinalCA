<template>
  <div class="cardContainer">
    <div v-for="card in cards">
      <router-link :to="{ name: 'card', params: { id: card.name}}">
      
      <img :src="card.imageUrl">
      </router-link>   
      
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    cards: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .cardContainer{
    display: flex;
    justify-content: space-evenly;
    flex-wrap: wrap;
    margin:0 auto;
    max-width: 1000px;
    & div{
      width: 150px;
      margin:20px;
      background-color: white;
      box-shadow:0px 0px 10px 6px white;
      &:hover{
        box-shadow:0px 0px 4px 4px white;
        background-color: white;
      }
    } 
  }

</style>
