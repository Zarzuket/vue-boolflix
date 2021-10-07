<template>
    <div class="card">
        <div class="info">
            <img :src="`http://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="Image Not Found">
            <div>
                <h4 class="title"><span>Titolo :</span>{{serie.name}}</h4>
                <h4><span>Titolo originale:</span> {{serie.original_name}}</h4>
                <h4 v-if="serie.original_language == 'it'"><span>Lingua:</span><img class="flag_img" src="../assets/img/it.svg" alt=""></h4>
                <h4 v-else-if="serie.original_language == 'en'"><span>Lingua:</span><img class="flag_img" src="../assets/img/en.jpg" alt=""></h4>
                <h4 v-else><span>Lingua:</span><img class="flag_img" src="../assets/img/Flag_missing.jpg" alt=""></h4>
                <h4><span>Voto:</span><div><i v-for="n in 5" :key="n" class="fa-star" :class="(n <= realVote()) ? 'fas' : 'far'"></i></div></h4>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name:"Serie",
    props: ["serie"],
data(){
    return{
        stars:[]
    }
},
methods:{
    realVote(){
        return Math.ceil(this.serie.vote_average / 2);
    }
}
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
        .flag_img{
            width: 15%;
        }
        img{
            width: 100%;
            
        }
    };
}


</style>