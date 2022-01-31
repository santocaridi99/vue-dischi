<template>
  <div id="app">
    <header></header>
    <main-container :disks="disks">
      <card-box></card-box>
    </main-container>
  </div>
</template>

<script>
import MainContainer from './components/MainContent.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    MainContainer
  },
  data(){
    return{
      disks:[],
    }
  },
  mounted(){
    // res sta per response 
    axios .get('https://flynn.boolean.careers/exercises/api/array/music').then((res)=>{
      // dischi sarà uguale al response del data però dell'array di oggetti chiamato response
      this.disks = res.data.response
    });
  }
}
</script>

<style lang="scss">

</style>
