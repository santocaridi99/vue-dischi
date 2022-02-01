<template>
  <div class="filterContainer">
    <!-- una select che accetta come v-model una variabile selectedgenre (genere selezionato) -->
    <!-- e al cambio ,evento verrà ascoltato da App che chiamerà il metodo relativo -->
    <!-- ovvero @genre=genreFilter -->
    <!-- riceve come parametro il dato inviato dal figlio (selectedGenre) -->
    <select v-model="selectedGenre" @change="$emit('genre', selectedGenre)">
      <option value="">All</option>
      <option v-for="(category, i) in genresArray" :key="i" :value="category">
        {{ category }}
      </option>
    </select>
    <!-- select autori -->
    <!-- v-model variabile selectedAuthor (autore selezionato) -->
    <!-- evento change verrà ascoltato da App che chiamerà il metodo corrispondente a artist
        @artist='artistFilter'
        e riceve come parametro il dato inviato dal figlio (selectedAuthor) -->

    <select v-model="selectedAuthor" @change="$emit('artist', selectedAuthor)">
      <option value="">All Authors</option>
      <option v-for="(artist, i) in authorsArray" :key="i" :value="artist">
        {{ artist }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    // chiamo le props  che sono array relativo a generi e array relativo ad autori
    genresArray: Array,
    authorsArray: Array,
  },
  data() {
    return {
      // variabile genere selezionato
      selectedGenre: "",
      // variabile autore selezionato
      selectedAuthor: "",
    };
  },
  // NON SERVE PIU' PERCHE' HO RESO TUTTO DINAMICO

  // methods: {
  //   selectGenre() {
  //     this.$emit("genre", this.selectedGenre);
  //   },
  //   selectAuthor(){
  //     this.$emit("artist",this.selectedAuthor)
  //   }
  // },
};
</script>

<style lang="scss" scoped>
@import "@/style/variables.scss";
.filterContainer {
  display: flex;
  width: 1200px;
  margin: 0 auto;
  height: 60px;
  justify-content: flex-end;
  align-items: center;
}
</style>