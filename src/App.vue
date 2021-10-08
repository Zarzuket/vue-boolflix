<template>
  <div id="app">
    <Header @sendsearch="sendsearch"/>
    <Main :resultsearch="resultsearch"/>
    <SerieTv :resultsearch="resultsearch"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import SerieTv from "./components/SerieTv.vue"

export default {
  name: 'App',
  components: {
    Header,
    Main,
    SerieTv
    

  },
  data(){
    return{
      resultsearch:"",
    }
  },
  methods:{
    sendsearch(abba){
      this.resultsearch = abba;
    }
  }
}
</script>

<style lang="scss">
@import "./assets/style/common.scss";
@import '~@fortawesome/fontawesome-free/css/all.css';
#app{
  background-color: rgb(20, 20, 20);
}
</style>
