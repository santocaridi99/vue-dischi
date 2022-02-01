<template>
  <div id="app">
    <!-- sezione header -->
    <header-box></header-box>
    <!-- sezione filter -->
    <!-- genresarray corrisponderà a filteredgeneres -->
    <!-- authors array corrisponderà a filtered authors -->
    <!-- genre chiamerà il metodo genreFilters in methods -->
    <!-- artist chiamerà artistFilter -->
    <filter-section
      :genresArray="filteredGenres"
      :authorsArray="filteredAuthors"
      @genre="genreFilter"
      @artist="artistFilter"
    ></filter-section>
    <!-- loader compare solo se flag loader è falso -->
    <loader-content v-if="!flagLoader"></loader-content>
    <!-- sezione main -->
    <!-- compare solo se flagloader è vero -->
    <!-- avrà come props i dischi(disks)filtrati  presenti nell'array filteredDisks -->
    <main-content v-else :disks="filteredDisks">
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
// importo loader content
import LoaderContent from "./components/LoaderContent.vue";

export default {
  name: "App",
  components: {
    MainContent,
    HeaderBox,
    FilterSection,
    LoaderContent,
  },
  data() {
    return {
      // array di dischi
      disks: [],
      // array filtrato
      filteredDisks: [],
      // flag per indicare il valore di loader
      flagLoader: false,
      // array degli artisti filtrati
      filteredAuthors: [],
      // array dei generi filtrati
      filteredGenres: [],
    };
  },
  methods: {
    // metodo per filtrare per genere
    // keyword corrisponderà al parametro che verrà passato dal figlio filteredsection
    // ovvero in questo caso selectedGenre
    genreFilter(keyword) {
      this.filteredDisks = this.disks.filter((disk) => {
        return disk.genre.includes(keyword);
      });
    },
    // ugualmente metodo per filtrare gli artisti
    artistFilter(keyword) {
      this.filteredDisks = this.disks.filter((disk) => {
        return disk.author.includes(keyword);
      });
    },
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
          // stessa cosa filteredDisks
          this.filteredDisks = res.data.response;
          // quando carica l'array diventa true
          this.flagLoader = true;
          // pusho nell' array filteredGenres  i vari elementi filtrati per genere
          this.disks.forEach((element) => {
            if (!this.filteredGenres.includes(element.genre)) {
              this.filteredGenres.push(element.genre);
            }
          });
          // pusho nell' array filteredAuthors i vari elementi filtrati per autore
          this.disks.forEach((element) => {
            if (!this.filteredAuthors.includes(element.author)) {
              this.filteredAuthors.push(element.author);
            }
          });
        });
    }, 2000);
  },
};
</script>

<style lang="scss">
// importo cartella main scss
@import "./style/main.scss";
</style>
