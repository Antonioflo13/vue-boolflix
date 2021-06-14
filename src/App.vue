<template>
  <div id="app">
    <Header @search="searchValue"/>
    <Main :films=films />
    <Footer/>

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Footer from './components/Footer.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Footer
  },
  data () {
    return {
      apiMovies: "https://api.themoviedb.org/3/search/movie",
      apiTvShows: "https://api.themoviedb.org/3/search/tv",
      idApi: "3890dce83d488cedadba197d9aad9826",
      films: [],
      search: ""
    }
  },
  methods: {
    searchValue(value) {
      this.callServer()
      this.search = value;
    },
  callServer() {
    axios 
      .get( `${this.apiMovies}?`,{
        params: {
          api_key: this.idApi,
          query: this.search
        }
      }) 
      .then(
        (response) => {
          this.films = response.data.results;
        }
      )
      .get( `${this.apiTvShows}?`,{
        params: {
          api_key: this.idApi,
          query: this.search
        }
      }) 
      .then(
        (response) => {
          this.films = response.data.results;
        }
      )
  } 
  },
}
</script>

<style lang="scss">
  @import './style/general.scss';
</style>
