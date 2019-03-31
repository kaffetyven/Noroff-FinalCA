<template>
  <div class="about">
       <div class="about__top" v-on:click="click">
          <div class="chevron"></div>
          
          <div> <h2>Defeat your opponent</h2> </div>
          
          <div class="chevron--open" v-if="visible"><img src="../assets/chevron.svg"></div>        
          <div class="chevron" v-else><img src="../assets/chevron.svg"></div>  
           
        </div>
        <div class="about__bottom" v-if="visible">
       <p>
            Each player starts the game with 20 life. Knock your opponent down to 0 life, and you win.
            The most common way to do this is to summon creatures and attack with them.<br><br>
            Creature cards are the most important part of many Something decks. 
            They’re really easy to spot--just look at the lower right of a card.
            If you see a pair of numbers seperated by a stash, you’ve got a creature card.
            Once it’s on the battlefield, a creature continues to attack and defend for you until your opponent can find a way to take it out.<br><br>
            Most games become a race to see who can deal the most damage first.
            Summoning the best creatures will help you win that race every time. 
            Check out the section on casting creature spells.
          </p>
        </div>
  </div>
</template>

<script>
export default {
  name: 'About',
  props: {
    visible: Boolean
  },
  methods: {
    click(){      
      const app= this;
      app.$emit('click')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .about{
    max-width: 1000px;
    margin:0 auto;
    &__top{
     background-color: #DB1A2D;
     padding: 20px;     
     display: flex;
     justify-content: space-between;   
     align-items: center;     
     & h2{
       margin: 0;
       
       
     }
    }
    &__bottom{
      padding: 20px;
      background-image: url('../assets/bg-box.svg');
      background-size: cover;
      background-repeat: no-repeat;
    }
  }
  .chevron{
    width:50px; 
    user-select: none;   
    &--open{
      width: 50px;      
      transform: rotate(90deg);
      user-select: none;
    }  
  }
  .search{
    display: flex;
    background-color: #DB1A2D;
    margin:0 auto;
    max-width: 1000px;
    justify-content: center;
    & .search__bar{
      width:80%;
      & input{
        width:100%;
        border-radius: 5px;        
        border: none;    
        height:20px;
        margin:10px;
        padding:5px;
      }
    }
  }
</style>
