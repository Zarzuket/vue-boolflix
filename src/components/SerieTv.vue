<template>
    <div>

        <div class="container">
            <Serie :serie="element" v-for="(element,index) in serieTv" :key="index"/>
      <!-- <p>{{resultsearch}}</p> -->
        </div>
    </div>
</template>

<script>
import Serie from "./Serie.vue"
import axios from "axios"

export default {
    name: "SerieTv",
    props:["resultsearch"],
    components:{
        Serie,
    },
    data(){
        return{
            serieTv: []
        }
    },
    watch:{
            resultsearch: function(){
            axios.get('https://api.themoviedb.org/3/search/tv', {
            params: {
                api_key: "524f90be698385fdda5e6bb6a3c59608",
                query: this.resultsearch,
                lenguage: "it-IT" 
        }
    })
        .then((resp) =>{
            this.serieTv = resp.data.results;
            console.log(this.serieTv);
        })
    }
    }
    
}
</script>

<style lang="scss" scoped>
.container{
    display: flex;
    p{
        color: red;
    }
    height: 200px;
    width: 200px;
}
</style>