<template>
    <div class="flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <!-- <img :src="`http://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="Image Not Found"> -->
                <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`">
                <img v-else src="../assets/img/no_image.jpg" alt="">
            </div>
            <div class="flip-card-back">
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
.flip-card {
    background-color: transparent;
    margin: 1.875rem;
    width: calc((100% / 4) - 15rem);
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
  .flag_img{
      width: 15%;
  }
  img{
      width: 100%;
  }
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
}

/* Style the back side */
.flip-card-back {
  background-color: dodgerblue;
  color: black;
  transform: rotateY(180deg);
}
</style>