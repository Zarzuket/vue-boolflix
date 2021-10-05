<template>
  <div>
      <div class="abc">
          <Film :info="element" v-for="(element,index) in filmsEmpty" :key="index"/>
          <p>{{resultsearch}}</p>
      </div>
  </div>
</template>

<script>
import axios from "axios"
import Film from "./Film.vue"
export default {
    name:"Main",
    props:["resultsearch"],
    components:{
        Film,

    },
    data(){
        return{
            filmsEmpty: []
        }
    },
    updated(){
        axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
            api_key: "524f90be698385fdda5e6bb6a3c59608",
            query: this.resultsearch,
            lenguage: "it-IT" 
        }
    })
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