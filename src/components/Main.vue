<template>
  <div>
    <div class="cocontainer">
        <div>
            <h2>Film</h2>
        </div>
    </div>
      <div class="container">
          <Film :info="element" v-for="(element,index) in filmsEmpty" :key="index"/>
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
    watch:{
    resultsearch: function(){
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
}


</script>

<style lang="scss" scoped>
.cocontainer{
    display: flex;
    justify-content: space-around;
    h2{
        font-size: 4.875rem;
        color: red;
        box-shadow: 5px 10px 18px red;
    }
}
.container{
    display: flex;
    flex-wrap: wrap;
    p{
        color: red;
    }
}
</style>