<template>
    <div class="card">
        <div class="info">
            <img :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`" alt="Image Not Found">
            <div>
                <h4 class="title"><span>Titolo :</span>{{info.title}}</h4>
                <h4><span>Titolo originale:</span> {{info.original_title}}</h4>
                <h4 v-if="`${info.original_language} == 'ita'`"><span>Lingua:</span><img src="../assets/img/it.svg" alt=""></h4>
                <h4 v-else-if="`${info.original_language} == 'en'`"><span>Lingua:</span><img src="../assets/img/en.jpg" alt=""></h4>
                <h4 v-else><span>Lingua:</span><img src="../assets/img/missing_flag.jpg" alt=""></h4>
                
                <h4><span>Voto:</span> {{info.vote_average}}</h4>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name:"Film",
    props: ["info"],
}   
</script>

<style lang="scss" scoped>
span{
    color: red;
    font-size: 20px;
}
.card{
    border: 1px solid red;
    margin: 1.875rem;
    width: calc((100% / 4) - 15rem);
    .info{
        height: 100%;
        width: 100%;
        // overflow-y: auto;
        img{
            width: 100%;
            
        }
    }
}
</style>