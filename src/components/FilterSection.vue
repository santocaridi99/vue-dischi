<template>
<!-- una select che accetta come v-model una variabile selectedgenre (genere selezionato) -->
<!-- e al cambio chiama metodo select genre (seleziona genere) -->
  <select v-model="selectedGenre" @change="selectGenre">
    <option value="">All</option>
    <option value="Rock">Rock</option>
    <option value="Pop">Pop</option>
    <option value="Jazz">Jazz</option>
    <option value="Metal">Metal</option>
  </select>
 
</template>

<script>
export default {
  data() {
    return {
      // variabile genere selezionato
      selectedGenre:'',
    };
  },
  methods:{
    // il metodo seleziona genere
    // l'evento verrà ascoltato da App che chiamerà  il metodo corrispondente a genre
    // @genre='genreFiltered'
    // e riceve come parametro il dato inviato dal figlio (selectedGenre)
    selectGenre(){
      this.$emit('genre',this.selectedGenre)
    }
  }
};
</script>

<style lang="scss" scoped>
</style>