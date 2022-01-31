<template>
    <div class="container">
        <!-- v-for per ogni oggetto disco presente in dischi con chiave l'id unvico presente nel disco-->
        <card-box v-for="disk in disks" :key="disk.id" :disk="disk"></card-box>
    </div>
</template>

<script>
// importo cardbox
import CardBox from "./CardBox.vue"
export default {
    // esporto i componenti a  cardbox
    components:{
        CardBox,
    },
    // props  dischi corrisponde ad un array
    props:{
        disks:Array,
    }
}
</script>
<style lang="scss" scoped>

</style>