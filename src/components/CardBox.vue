<template>
<!-- carta(card) formata da immagine e un area texbox con titolo(title) autore(author) e anno dell'album(year) -->
    <div class="card">
        <img :src="disk.poster" :alt="disk.title">
        <div class="textbox">
            <h2>{{disk.title}}</h2>
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
// importo le variabili
@import '@/style/variables.scss';
.card{
    // width è tutto il container diviso 5 per riga e -20 px di margini destra e sinistra
width: calc(100% / 5 - 20px);
padding: 20px;
border-radius: 5px;
margin: 10px;
background-color: $pricipalitems;
img{
    width: 100%;
    // altezza fissa immagini
    height: 188px;
    margin-bottom: 10px;
}
.textbox{
    text-align: center;
    // area texbox è il 100% -  grandezza immagine
    height: calc(100% - 188px);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    h2{
        color: $whitetextcolor;
    }
    .author-year{
        color: $secondarytextcolor;

    }
   
}
}
</style>