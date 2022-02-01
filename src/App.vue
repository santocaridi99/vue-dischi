<template>
  <div id="app">
    <!-- sezione header -->
    <header-box></header-box>
    <!-- sezione filter -->
    <!-- genre chiamerà il metodo genreFilters in methods -->
    <filter-section @genre='genreFilter'></filter-section>
    <!-- sezione main -->
    <!-- avrà come props i dischi(disks)filtrati  presenti nell'array filteredDisks -->
    <main-content :disks="filteredDisks">
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
// importo filtersection
import FilterSection from "./components/FilterSection.vue";

export default {
  name: "App",
  components: {
    MainContent,
    HeaderBox,
    FilterSection,
  },
  data() {
    return {
      // array di dischi
      disks: [],
      // array filtrato
      filteredDisks:[]
    };
  },
  methods:{
    // metodo per filtrare per genere
    // keyword corrisponderà al parametro che verrà passato dal figlio filteredsection
    // ovvero in questo caso selectedGenre
    genreFilter(keyword){
      this.filteredDisks=this.disks.filter((disk)=>{
        return(disk.genre.includes(keyword))
      })
    }

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
          this.filteredDisks=res.data.response
        });
    }, 2000);
  },
};
</script>

<style lang="scss">
// importo cartella main scss
@import "./style/main.scss";
</style>
