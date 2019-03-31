<template>
  <div class="formMessage">    
      <h2>Success!</h2>
      <p>
        Thank you <b>{{name}}</b> for contacting us! <br><br>
      </p>
  </div>
</template>

<script>
export default {
  name: 'FormSent',
  props:{
    name: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.formMessage{
  text-align: center;
  margin: 0 auto;
  max-width: 940px;
  background-image: url('../assets/bg-box.svg');
  background-size: cover;
  background-repeat: no-repeat; 
  padding:30px;  
}
</style>
