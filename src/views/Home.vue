<template>
  <div class="home">
    <NavBar/>
    <Search
      @userInput="filterCards"
    />
    <h2>{{message}}</h2>
    <Card v-bind:cards="filtercards"/>
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/navbar.vue';
import Card from '@/components/card.vue';
import Search from '@/components/search.vue';



export default {
  name: 'home',
  components: {
    NavBar,
    Card,
    Search
  },

  data(){
    return{
      cards: [],
      filtercards: [],
      query: '',
      message: 'Click a card to view more'
      
    }
  },
  methods: {
    filterCards(input){
      const app = this;
      app.query = input.toLowerCase();
      if(app.query == ''){
        app.filtercards = app.cards
        app.message = "Click a card to view more"
      }else{
        app.filtercards = app.cards.filter(app.test);
        app.message = "Click a card to view more"   
        }
      if(app.filtercards == ''){
        app.message = "No cards found with your search:" + app.query;
      }
      },
      test(value){
        const app = this;
        var uni = value.name.toLowerCase();
        return uni.includes(app.query);
      }

    
  },  
  created(){
    const app = this;    
    fetch('https://api.magicthegathering.io/v1/cards')
    .then(function(response) {    
      return response.json();      
    })
    .then(function(myJson){      
      //app.cards = myJson.cards;
      for(var card in myJson.cards){
        //console.log(myJson.cards[card])
        if (myJson.cards[card].imageUrl != undefined){
          app.cards.push(myJson.cards[card])
          app.filtercards.push(myJson.cards[card]);
        }
        }     
      //console.log(app.cards);
    });
  }  
  
}
</script>

<style scoped lang="scss">  
  h2{
    text-align: center;
    -webkit-text-stroke: black 1px;
  }
</style>
