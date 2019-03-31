<template>
  <div class="">
    <LoginForm 
      @clicked="handleLogin"
      v-bind:message="message"
    />  
  </div>
</template>

<script>
import LoginForm from '@/components/loginform.vue'
//import { userInfo } from 'os';

export default {
  name: 'Login',
  components: {
    LoginForm
  },data(){
    return{
      sessionId: 'test',
      message: '',
    }
  },
  created(){ 
    localStorage.setItem('user', 'morten');
    localStorage.setItem('password', '123')
  },
  
  methods: {
    sessionGen(){
      const app = this;
      app.sessionId = Math.floor((Math.random() * 10000) + 1);
    },
    handleLogin(username, password){
      const app = this;
      if(localStorage.getItem('user')== username || localStorage.getItem('password') == password){        
        app.sessionGen();
        sessionStorage.setItem('sessionId', app.sessionId )
        app.$router.push('home');
        }else{
          app.message = "incorrect login details"
        }
      
    }
  }
}
</script>

<style scoped lang="scss">
 
</style>
