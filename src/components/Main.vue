<template>
  <div>
      <div class="abc">
          <p>{{resultsearch}}</p>
      </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
    name:"Main",
    props:["resultsearch"],
    components:{
        // Film

    },
    data(){
        return{
            filmsEmpty: []
        }
    },
    updated(){
        axios.get("https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro")
        .then((resp) =>{
            this.filmsEmpty = resp.data.results;
            console.log(this.filmsEmpty);
        })
    }
}
</script>

<style lang="scss" scoped>
.abc{
    p{
        color: red;
    }
    height: 200px;
    width: 200px;
}
</style>