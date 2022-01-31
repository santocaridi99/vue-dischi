<template>
  <div class="container">
    <!-- v-for per ogni oggetto disco presente in dischi con chiave l'id unvico presente nel disco-->
    <!-- passo la props disk che la chiamo disk, il singolo oggetto -->
    <card-box v-for="disk in disks" :key="disk.id" :disk="disk"></card-box>
    <!-- loader content è visibile solo se l'array disk è minore di 10 -->
    <loader-content v-if="disks.length < 10"></loader-content>
  </div>
</template>

<script>
// importo cardbox
import CardBox from "./CardBox.vue";
// import di loader content
import LoaderContent from "./LoaderContent.vue";
export default {
  // esporto i componenti a  cardbox
  components: {
    CardBox,
    LoaderContent,
  },
  // props  dischi corrisponde ad un array
  props: {
    disks: Array,
  },
};
</script>
<style lang="scss" scoped>
.container {
  width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}
</style>