<template>
    <div class="card">
        <div class="info">
            <img :src="`http://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="Image Not Found">
            <div>
                <!-- <h4 class="title"><span>Titolo :</span>{{serie.name}}</h4>
                <h4><span>Titolo originale:</span> {{serie.original_title}}</h4> -->
                <h4 v-if="`${serie.original_language} == 'it'`"><span>Lingua:</span><img src="../assets/img/it.svg" alt=""></h4>
                <h4 v-else-if="`${serie.original_language} == 'en'`"><span>Lingua:</span><img src="../assets/img/en.jpg" alt=""></h4>
                <h4 v-else><span>Lingua:</span><img src="../assets/img/missing_flag.svg" alt=""></h4>
                
                <!-- <h4><span>Voto:</span> {{serie.vote_average}}</h4> -->
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name:"Serie",
    props: ["serie"],
}   

</script>

<style lang="scss" scoped>
span{
    color: red;
    font-size: 20px;
}
.card{
    border: 1px solid green;
    margin: 1.875rem;
    width: calc((100% / 4) - 15rem);
    .info{
        height: 100%;
        width: 100%;
        img{
            width: 100%;
        }
    };
}
</style>