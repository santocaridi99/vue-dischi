<template>
    <div class="container">
        <card-box v-for="disk in disks" :key="disk.id" :disk="disk"></card-box>
    </div>
</template>

<script>
import CardBox from "./CardBox.vue"
export default {
    components:{
        CardBox,
    },
    props:{
        disks:Array,
    }
}
</script>
<style lang="scss" scoped>

</style>