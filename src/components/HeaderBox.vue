<template>
    <header>
        <!-- header  ha logo con img interna -->
       <div class="logo">
            <img src="@/assets/logo.svg" alt="spotify">
       </div>
    </header>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';
header{
    height: 60px;
    background-color:$pricipalitems;
    margin-bottom: 50px;
    padding: 20px;
    .logo{
        width: 90px;
        img{
            width: 100%;
            height: 100%;
        }
    }
}
</style>