<template>
  <div class="">
    <NavBar/>   
    <CardSpecific v-bind:card="card"/>
  </div>
</template>

<script>
import NavBar from '@/components/navbar.vue';
import CardSpecific from '@/components/cardSpecific.vue'

export default {
  name: 'card',
  components: {
    NavBar,
    CardSpecific
  },
  data(){
    return{
      cards: [],
      card: {}
    }
  },

  created(){
    const app = this;
    var param = app.$route.params.id;
    //console.log(param);
    fetch('https://api.magicthegathering.io/v1/cards')
    .then(function(response) {    
      return response.json();      
    })
    .then(function(myJson){      
      //app.cards = myJson.cards;
      for(var card in myJson.cards){
       // console.log(myJson.cards[card])
        if (myJson.cards[card].imageUrl != undefined){
          app.cards.push(myJson.cards[card]);
        }
        }
      for(var i in app.cards){
        if(app.cards[i].name == param){
          app.card = app.cards[i];
        }
      }
              
      
      console.log(app.card);
    });
  }
}

</script>

<style scoped lang="scss">
 
</style>
