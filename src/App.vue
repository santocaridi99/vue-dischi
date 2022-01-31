<template>
  <div id="app">
    <!-- sezione header -->
    <header-box></header-box>
    <!-- sezione main -->
    <main-container :disks="disks">
      <!-- sezione card box -->
      <card-box></card-box>
    </main-container>
  </div>
</template>

<script>
// importo componente  Maincontainer 
import MainContainer from './components/MainContent.vue'
// importo axios per effettuare chiamate api
import axios from 'axios'
// importo header
import HeaderBox from './components/HeaderBox.vue'

export default {
  name: 'App',
  components: {
    MainContainer,
    HeaderBox
  },
  data(){
    return{
      // array di dischi
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
// importo cartella main scss
@import "./style/main.scss"
</style>
