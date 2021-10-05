<template>
  <div id="app">
    <Header @sendsearch="sendsearch"/>
    <Main :resultsearch="resultsearch"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"

export default {
  name: 'App',
  components: {
    Header,
    Main
    

  },
  data(){
    return{
      resultsearch:"",
    }
  },
  methods:{
    sendsearch(abba){
      this.resultsearch = abba;
      console.log(this.resultsearch)
    }
  }
}
</script>

<style lang="scss">
</style>
