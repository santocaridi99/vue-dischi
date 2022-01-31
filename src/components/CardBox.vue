<template>
<!-- carta formata da immagine e un area texbox con titolo autore e anno dell'album -->
    <div class="card">
        <img :src="disk.poster" :alt="disk.title">
        <div class="textbox">
            <h1>{{disk.title}}</h1>
            <div class="author-year">
                <h3>{{disk.author}}</h3>
                <h4>{{disk.year}}</h4>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    // disck è un oggetto
    props:{
        disk:Object,
    }
}
</script>
<style lang="scss" scoped>

</style>