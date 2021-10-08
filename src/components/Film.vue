<template>
    <div class="card">
        <div class="show">
            <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`">
            <img v-else src="../assets/img/no_f_img.png" alt="" >
        </div>
            <div class="card_info">
                <h4 class="title"><span>Titolo :</span>{{info.title}}</h4>
                <h4><span>Titolo originale:</span> {{info.original_title}}</h4>
                <h4 v-if="info.original_language == 'it'"><span>Lingua:</span><img class="flag_img" src="../assets/img/it.svg" alt=""></h4>
                <h4 v-else-if="info.original_language == 'en'"><span>Lingua:</span><img class="flag_img" src="../assets/img/en.jpg" alt=""></h4>
                <h4 v-else><span>Lingua:</span><img class="flag_img" src="../assets/img/Flag_missing.jpg" alt=""></h4>
                <h4><span>Voto:</span><div><i v-for="n in 5" :key="n" class="fa-star" :class="(n <= realVote()) ? 'fas' : 'far'"></i></div></h4>
            </div>
    </div>
</template>

<script>


export default {
    name:"Film",
    props: ["info"],
methods:{
    realVote(){
        return Math.ceil(this.info.vote_average / 2);
    }
}   
}
</script>


<style lang="scss" scoped>
.card{
    overflow: hidden;
    position: relative;
    height: 100%;
    margin: 1.525rem .625rem;
    
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
        border: .0625rem solid red;
    }
.card_info:hover{
    opacity: 1;
    padding: 1.25rem;
    color: white;
}
span{
    color: red;
    font-size: 1.25rem;
}
.abc{
    height: 100%;
    width: 100%;
}
</style>