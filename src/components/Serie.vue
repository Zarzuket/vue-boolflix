<template>
    <div class="card">
        <div class="show">
            <img :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" :alt="serie.name">
            <!-- <img v-else src="../assets/img/no_image.jpg" alt=""> -->
        </div>
        <div class="card_info">
            <h4 class="title"><span>Titolo :</span>{{serie.name}}</h4>
            <h4><span>Titolo originale:</span> {{serie.original_name}}</h4>
            <h4 v-if="serie.original_language == 'it'"><span>Lingua:</span><img class="flag_img" src="../assets/img/it.svg" alt=""></h4>
            <h4 v-else-if="serie.original_language == 'en'"><span>Lingua:</span><img class="flag_img" src="../assets/img/en.jpg" alt=""></h4>
            <h4 v-else><span>Lingua:</span><img class="flag_img" src="../assets/img/Flag_missing.jpg" alt=""></h4>
            <h4><span>Voto:</span><div><i v-for="n in 5" :key="n" class="fa-star" :class="(n <= realVote()) ? 'fas' : 'far'"></i></div></h4>
        </div>
    </div>
</template>

<script>


export default {
    name:"Serie",
    props: ["serie"],
methods:{
    realVote(){
        return Math.ceil(this.serie.vote_average / 2);
    }
}
}
</script>

<style lang="scss" scoped>

.card{
    overflow: hidden;
    position: relative;
    height: 100%;
    

    .flag_img{
        width: 15%;
    }

    .show {
    display: flex;
    height: 100%;

    img {
        object-fit: cover;
        width: 100%;
    }

}
}
    .card_info {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        background: rgba(0,0,0,0.8);
        opacity: 0;
    }

.card_info:hover{
    opacity: 1;
}

span{
    color: red;
    font-size: 20px;
}

// .card_info{
//     display: none;
// }
// .card:hover .show{
//     display: none;
// }
</style>