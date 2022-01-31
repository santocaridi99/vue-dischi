<template>
  <div id="app">
    <!-- sezione header -->
    <header-box></header-box>
    <!-- sezione main -->
    <main-content :disks="disks">
      <!-- sezione card box -->
      <card-box></card-box>
    </main-content>
  </div>
</template>

<script>
// importo componente  Maincontainer
import MainContent from "./components/MainContent.vue";
// importo axios per effettuare chiamate api
import axios from "axios";
// importo header
import HeaderBox from "./components/HeaderBox.vue";

export default {
  name: "App",
  components: {
    MainContent,
    HeaderBox,
  },
  data() {
    return {
      // array di dischi
      disks: [],
    };
  },
  mounted() {
    // messo un set timeout così riempie l'array dopo due secondi
    setTimeout(() => {
      // res sta per response
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((res) => {
          // dischi sarà uguale al response del data però dell'array di oggetti chiamato response
          this.disks = res.data.response;
        });
    },2000);
  },
};
</script>

<style lang="scss">
// importo cartella main scss
@import "./style/main.scss";
</style>
