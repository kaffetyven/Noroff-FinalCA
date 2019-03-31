<template>
  <div id="app">
    <div class="logo__container">
      <div><img alt="logo" class="logo" src="./assets/magiclogo.png"></div>      
    </div>
    
    <router-view/>    
    <div class="footer__text">
      <span >WallemDesign</span>
    </div>
  </div>
</template>
<script>
export default {
  name: 'app',
  components: {
    
  },
  methods: {
    checkLogin(){
      if(sessionStorage.getItem("sessionId") == undefined){
        this.$router.push({name: 'login'})
      }
    }
  },
  created(){
    const app = this;
    app.checkLogin();
  },
  beforeUpdate(){
    const app = this;
    app.checkLogin();
  }
}
</script>

<style lang="scss">
html { 
  background: url(assets/bg.jpg) no-repeat center center fixed; 
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;  
  color: white;
}
img{
  width:100%;
}
.logo{
  max-width: 400px;  
  &__container{
    display: flex;
    justify-content: center;
    margin-top: 30px;
    margin-bottom: 15px;
  }
}
.footer__text{  
  position: fixed;
  bottom:0;
  text-align: center;
  width:97%;  
  padding-bottom: 2px;
  background-color:#DB1A2D;;
}
a{
  text-decoration-line: none;
  color:white;
  font-weight: bold;
  font-size: 1.8em;
  -webkit-text-stroke: black 1px;
  &.router-link-exact-active{
    color:red;
  }
  
}

</style>
