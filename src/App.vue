<template>
  <div id="app">
    <Header @search="searchValue"/>
    <Main :films=films :populars=populars :topRateds="topRateds" />
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Footer from './components/Footer.vue';
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
      apiMostPopular: "https://api.themoviedb.org/3/movie/popular",
      apiTopRated: "https://api.themoviedb.org/3/movie/top_rated",
      idApi: "3890dce83d488cedadba197d9aad9826",
      films: [],
      populars: [],
      topRateds: [],
      search: ""
    }
  },
  methods: {
    searchValue(value) {
      this.search = value;
      this.callServer()
    },
  callServer() {
    axios.all([
      axios.get( `${this.apiMovies}?`,{
        params: {
          api_key: this.idApi,
          query: this.search
        }
      }),
      axios.get( `${this.apiTvShows}?`,{
          params: {
          api_key: this.idApi,
          query: this.search
        }
      })
      .then(
        (response) => {
          this.films = response.data.results.slice(0,6);
        }
      )
      .catch(
        function (error) {
          console.log(error);
        }
      ) 
    ])
  } 
  },
  created() {
    axios.all([
      axios.get( `${this.apiMostPopular}?`,{
          params: {
          api_key: this.idApi,
          languages: '=it-IT',
        }
      })
      .then(
        (response) => {
          this.populars = response.data.results.slice(0,6);
        }
      ),
      axios.get( `${this.apiTopRated}?`,{
          params: {
          api_key: this.idApi,
          languages: '=it-IT',
          page: 1
        }
      })
      .then(
        (response) => {
          this.topRateds = response.data.results.slice(0,6);
        }
      )

    ]) 
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
</style>
