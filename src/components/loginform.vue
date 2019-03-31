<template>
  <div class="form">    
    <h1>Login</h1>
    <form>
    <div class="form__container">    
      <div class="form__input">
        <span>Username:</span>
        <input name="username" v-model="username">
      </div>
      <div class="form__input">
        <span>Password:</span>
        <input name="password" type="password" v-model="password">
      </div>
      <div class="form__submit">
        <span class="error"> {{message}}</span>
        <button class="button" type="button" v-on:click="login">Submit</button>
      </div>      
    </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginForm',
  props: {
    message: String
  },
  methods: {
    login(){
      
      const app= this;
      app.$emit('clicked', app.username, app.password)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.form{
  margin: 0 auto;
  max-width: 800px;
  background-image: url('../assets/bg-box.svg');
  background-size: cover;
  background-repeat: no-repeat;
  padding-top: 10px;
  
  & h1{
    text-align: center;
    margin:0px;
  }
}
.form__container{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.form__input{
  display: flex;
  justify-content:flex-end;
  align-items: center;
  width:80%;
  margin:20px;
  & input{
    width:100%;
    border-radius: 5px;
    border: none;
    margin-left: 10px;
    height:20px
  }
  & span{
    width:20%;
    
  }
}
.button{
  background-image: url('../assets/button.svg');
  background-size: cover;
  background-repeat: no-repeat;
  font-size: 1.5em;
}
.form__submit{
  display: flex;
  width:80%; justify-content: space-between;
  margin:20px;
  & button{
    width:30%;
    height: 60px;
    border: none;
    background-color: transparent;
    color:white;
  }
  & span{
    color:  #DB1A2D;
  }
}
</style>
