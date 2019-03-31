<template>
  <div class="hello">
    <div class="nav">
      
      <router-link to="/home"><div>Home</div></router-link>
      <router-link to="/about"><div>About</div></router-link>
      <router-link to="/contact"><div>Contact</div></router-link>         
    </div> 
  </div>
</template>

<script>
export default {
  name: 'NavBar',
  props: {
    name
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.nav{    
    margin:0 auto;
    max-width: 1000px;
    min-height: 50px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;    
    background-image: url('../assets/bg-tab.svg');
    background-size: cover;
    background-repeat: no-repeat;    
  } 
</style>
