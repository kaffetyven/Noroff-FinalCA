<template>
  <div class="form">    
    <h1>Contact</h1>
    <form v-on:submit.prevent="sendForm">
    <div class="form__container">    
      <div class="form__input">
        <span>Name:</span>
        <input name="username" v-model="name" v-on:keyup="sendName" v-on:blur="sendName" v-bind:class="{ error: nameError, valid: validName }">
      </div>
      <div class="form__error"><span class="air"></span><span v-if="nameError">This field can't be blank</span> </div>
      <div class="form__input">
        <span>Lastname:</span>
        <input name="lastname"  v-model="lastName" v-on:keyup="sendLastName" v-on:blur="sendLastName" v-bind:class="{ error: lastNameError, valid: validLastName }">
      </div>
      <div class="form__error"><span class="air"></span><span v-if="lastNameError">This field can't be blank</span> </div>
      <div class="form__input">
        <span>Email:</span>
        <input name="email"  v-model="email" v-on:keyup="sendEmail" v-on:blur="sendEmail" v-bind:class="{ error: emailError, valid: validEmail }">
      </div>
      <div class="form__error"><span class="air"></span><span v-if="emailError">Not a valid Email</span> </div>
      <div class="form__input">
        <span>Number:</span>
        <input name="number"  v-model="number" v-on:keyup="sendNumber" v-on:blur="sendNumber" v-bind:class="{ error: numberError, valid: validNumber }">
      </div>
      <div class="form__error"><span class="air"></span><span  v-if="numberError">Invalid number format, must be: <br>XXX XXX XXXX <br>XXX-XXX-XXXX<br>XXX.XXX.XXXX</span> </div>
      
      
      
      
      <div class="form__submit">
        <span class="error"> {{message}}</span>
        <button class="button" type="submit">Send</button>
      </div>      
    </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Contact',
  props: {
    nameError: Boolean,
    validName: Boolean,
    lastNameError: Boolean,
    validLastName: Boolean,
    emailError: Boolean,
    validEmail: Boolean,
    numberError: Boolean,
    validNumber: Boolean,
  },
  methods: {
    sendForm(){      
      const app= this;
      app.$emit('sendForm', app.name, app.lastName, app.email, app.number)
    },
    sendName(){
      const app = this;
      app.$emit('sendName', app.name)
    },
    sendLastName(){
      const app = this;
      app.$emit('sendLastName', app.lastName)
    },
    sendEmail(){
      const app = this;
      app.$emit('sendEmail', app.email)
    },
    sendNumber(){
      const app = this;
      app.$emit('sendNumber', app.number)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.form{
  margin: 0 auto;
  max-width: 1000px;
  background-image: url('../assets/bg-box.svg');
  background-size: cover;
  background-repeat: no-repeat;
  padding-top: 10px;
  
  & h1{
    text-align: center;
    margin:0px;
    margin-top:10px;
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
    height:20px;
    &.error{
      border:solid #DB1A2D 2px;
    }
    &.valid{
      border:solid green 2px;
    }
  }
  & span{
    width:20%;
    
  }
}

.form__error{
  width:80%;
  display: flex;
  justify-content: flex-start;
  & .air{
    width:20%;
  }
  & span{
    color:#DB1A2D;
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
