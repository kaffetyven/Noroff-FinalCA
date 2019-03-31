<template>
  <div class="">
    <NavBar/>
    <Contact
      v-bind:nameError="nameError" v-bind:validName="validName" @sendName="validateName"
      v-bind:lastNameError="lastNameError" v-bind:validLastName="validLastName" @sendLastName="validateLastName"
      v-bind:emailError="emailError" v-bind:validEmail="validEmail" @sendEmail="validateEmail"
      v-bind:numberError="numberError" v-bind:validNumber="validNumber" @sendNumber="validateNumber"
      @sendForm="validateForm"
      v-if="!validForm"      
    /> 
    <FormSent v-bind:name="name" v-if="validForm"/>
  </div>
</template>

<script>
import NavBar from '@/components/navbar.vue'
import Contact from '@/components/contact.vue'
import FormSent from '@/components/formSent.vue'

export default {
  name: 'contact',
  components: {
    NavBar,
    Contact,
    FormSent
  },
  data(){
    return{
      nameError: false,
      validName: false,
      lastNameError: false,
      validLastName: false,
      emailError: false,
      validEmail: false,
      numberError: false,
      validNumber: false,
      name:'test',
      lastname:'',
      email:'',
      number: '',
      validForm: false

    }
  },
  methods: {
    validateName(name){
      const app = this;      
      if(name == "" || name == undefined){
        app.nameError = true;
        app.validName = false;
      }else{
        app.nameError = false;
        app.validName = true;
        }
    },
    validateLastName(lastName){
      const app = this;      
      if(lastName == "" || lastName == undefined){
        app.lastNameError = true;
        app.validLastName = false;
      }else{
        app.lastNameError = false;
        app.validLastName = true;
        }
    },
    validateEmail(email){
      const app = this;
      var emailpattern = /^\w.+@\w+\.\w+$/;   
      if(emailpattern.test(email) == false || email == undefined || email == ""){
        app.emailError = true;
        app.validEmail = false;
      }else{
        app.emailError = false;
        app.validEmail = true;
        }
    },
    validateNumber(number){
      const app = this;
      var numberpattern1 = /^\d{3}(\.|-|\s)\d{3}(\.|-|\s)\d{4}$/;
      if(numberpattern1.test(number) == false || number == undefined || number == ""){
        app.numberError = true;
        app.validNumber = false;
      }else{
        app.numberError = false;
        app.validNumber = true;
        }
    },
    validateForm(name, lastname, email, number){      
      const app = this;
      app.validateName(name);
      app.validateLastName(lastname);
      app.validateEmail(email);
      app.validateNumber(number);
      if(app.validName == true && app.validLastName == true && app.validEmail == true && app.validNumber == true){
        app.name = name;
        app.lastname = lastname;
        app.email = email;
        app.number = number;
        app.validForm = true;
      }
    }
  }
}
</script>

<style scoped lang="scss">
 
</style>
