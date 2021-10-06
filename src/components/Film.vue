<template>
    <div class="card">
        <div class="info">
            <img :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`" alt="">
            <!-- <img src=""  alt=""> -->
            <div>
                <h4 class="title"><span>Titolo :</span>{{info.title}}</h4>
                <h4><span>Titolo originale:</span> {{info.original_title}}</h4>
                <h4><span>Lingua:</span> {{info.original_language}}</h4>
                
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
    width: 12.5rem;
    height: 12.5rem;
    border: 1px solid red;
    .info{
        height: 100%;
        width: 100%;
        overflow-y: auto;
        img{
            width: 12.5rem;
            height: 12.5rem;
        }
    }
}
</style>