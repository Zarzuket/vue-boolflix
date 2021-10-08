<template>
    <div>
        <div class="cocontainer">
            <div>
                <h2>SERIE TV</h2>
            </div>
        </div>
            <div class="container">
                <Serie :serie="element" v-for="(element,index) in serieTv" :key="index"/>
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
            serieTv: [],
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
.cocontainer{
    display: flex;
    justify-content: center;
    h2{
        color: green;
        font-size: 4.875rem;
        color: green;
        box-shadow: 5px 10px 18px green;
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