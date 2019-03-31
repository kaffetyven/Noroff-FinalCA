<template>
  <div class="">
    <NavBar/>
    <About v-bind:visible="visible" @click="showHide"/>
  </div>
</template>

<script>
import NavBar from '@/components/navbar.vue'
import About from '@/components/about.vue'

export default {
  name: '',
  components: {
    NavBar,
    About
  },
  data(){
    return {
      visible: true
    }
  },
  methods: {
    showHide(){
     const app = this;
     if(app.visible == true){
       app.visible = false;
     }else{
       app.visible = true
     }
    }
  }
  
}
</script>

<style scoped lang="scss">
 
</style>
