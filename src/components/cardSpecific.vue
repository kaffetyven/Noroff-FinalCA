<template>
  <div class="specificCard">    
      <div class="img_container">
        <img :src="card.imageUrl">
      </div>
      <div class="text_container">
        <h2>{{card.name}}</h2>
        <p> Color: {{card.colors[0]}} <br> Text: {{card.text}} <br> Rarity: {{card.rarity}}</p>
      </div>
  </div>
</template>

<script>
export default {
  name: 'CardSpecific',
  props:{
    card: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.specificCard{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0 auto;
  max-width: 940px;
  background-image: url('../assets/bg-box.svg');
  background-size: cover;
  background-repeat: no-repeat;
  
  padding:30px;
  & .img_container{    
    width:30%;
    background-color: white;
    
    border: ridge 1px white;
    box-shadow:0px 0px 20px 20px white;
  }
  & .text_container{
    margin-left:30px;
    margin-right:30px;
    width:60%;
  }
}
</style>
