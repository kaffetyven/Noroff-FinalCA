<template>
  <div class="search">
       <div class="search__bar">
          <input placeholder="Search cards" v-on:keyup="search" v-model="input" type="text" name="search">
        </div>
       
  </div>
</template>

<script>
export default {
  name: 'Search',
  props: {
    
  },
  methods: {
    search(){      
      const app= this;
      app.$emit('userInput', app.input)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
