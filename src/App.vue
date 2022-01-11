<template>
  <div id="app">
    <Header @search="search" />
    <Main :allFilms="films" :allSeries="series" :movieGen="movieGenres" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      films: [],
      series: [],
      input: "",
      movieGenres: [],
      apiKey: 'cdcfe1113982652506af0e8193d0dd64',
      param: {
        language: 'it-IT'
      },
    }
  },
  created() {
    // RICHIESTA AXIOS PER FILM POPOLARI
    axios.get(`https://api.themoviedb.org/3/movie/popular?api_key=${this.apiKey}&language=en-US&page=1`, {
      params: this.param
    })
    .then( (resp) => {
      this.films = resp.data.results;
    }),
    // RICHIESTA AXIOS PER SERIE TV POPOLARI
    axios.get(`https://api.themoviedb.org/3/tv/popular?api_key=${this.apiKey}&language=en-US&page=1`, {
      params: this.param
    })
    .then( (resp) => {
      this.series = resp.data.results;
    }),
    // RICHIESTA AXIOS PER GENERI FILM
    axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=${this.apiKey}&language=en-US`, {
      params: this.param
    })
    .then( (resp) => {
      for (let i = 0; i < resp.data.genres.length; i++) {
        this.movieGenres.push(resp.data.genres[i]);
      }
      return console.log(this.movieGenres);
    })
  },
  methods: {
  search(userInput) {
    this.input = userInput;
    axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: this.apiKey,
        query: this.input ,
        language: 'it-IT'
      }
    })
      .then( (resp) => {
        this.films = resp.data.results;
        console.log(resp.data.results)
      })
    axios.get('https://api.themoviedb.org/3/search/tv', {
      params: {
          api_key: this.apiKey,
          query: this.input ,
          language: 'it-IT'
      }
    })
      .then( (resp) => {
        this.series = resp.data.results;
      })
    }
  }
}    
</script>

<style lang="scss">
@import './assets/style/common.scss';
@import '~@fortawesome/fontawesome-free/css/all.css';
// #app {
// }
</style>