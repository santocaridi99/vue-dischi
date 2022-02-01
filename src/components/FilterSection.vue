<template>
 <div class="filterContainer">
  <!-- una select che accetta come v-model una variabile selectedgenre (genere selezionato) -->
  <!-- e al cambio chiama metodo select genre (seleziona genere) -->
  <select v-model="selectedGenre" @change="selectGenre">
    <option value="">All</option>
    <option value="Rock">Rock</option>
    <option value="Pop">Pop</option>
    <option value="Jazz">Jazz</option>
    <option value="Metal">Metal</option>
  </select>
  <!-- select autori -->
  <!-- v-model variabile selectedAuthor (autore selezionato) -->
  <!-- al cambio chiama matodo selectAuthor (seleziona autore) -->
  <select v-model="selectedAuthor" @change="selectAuthor">
    <option value="">All Authors</option>
    <option value="Bon Jovi">Bon Jovi</option>
    <option value="Queen">Queen</option>
    <option value="Sting">Sting</option>
    <option value="Steve Gadd Band">Steve Gadd Band</option>
    <option value="Iron Maiden">Iron Maiden</option>
    <option value="Eric Clapton">Eric Clapton</option>
    <option value="Deep Purple">Deep Purple</option>
    <option value="Metallica">Metallica</option>
    <option value="Dave Weckl">Dave Weckl</option>
    <option value="Michael Jacjson">Michael Jacjson :D</option>
  </select>
 </div>
</template>

<script>
export default {
  data() {
    return {
      // variabile genere selezionato
      selectedGenre: "",
      selectedAuthor: "",
    };
  },
  methods: {
    // il metodo seleziona genere
    // l'evento verrà ascoltato da App che chiamerà  il metodo corrispondente a genre
    // @genre='genreFilter'
    // e riceve come parametro il dato inviato dal figlio (selectedGenre)
    selectGenre() {
      this.$emit("genre", this.selectedGenre);
    },
    // stessa cosa solo che metodo seleziona l'autore
    // evento verrà ascoltato da App che chiamerà il metodo corrispondente a artist
    // @artist='artistFilter'
    // e riceve come parametro il dato inviato dal figlio (selectedAuthor)
    selectAuthor(){
      this.$emit("artist",this.selectedAuthor)
    }
  },
};
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';
.filterContainer{
  display: flex;
  width: 1200px;
  margin: 0 auto;
  height: 60px;
  justify-content: flex-end;
  align-items: center;
}
</style>