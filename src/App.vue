<template>
  <div id="app">
    <Header @search="searchValue"/>
    <Main :films="films" :series="series" :populars="populars" :topRateds="topRateds" :soap="soap" :action="action"/>
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
      series: [],
      topRateds: [],
      soap: [],
      action: [],
      search: "",
    }
  },
  methods: {
    searchValue(value) {
      this.search = value.trim();
      if (!value == '') {
        this.callServer()
      } else {
        this.films = "";
      }
    },
  callServer() {
    axios.all([
      axios.get( `${this.apiMovies}?`,{
        params: {
          api_key: this.idApi,
          query: this.search
        }
      })
      .then(
        (response) => {
          this.films = response.data.results.slice(0,20);
        }
      ),
      axios.get( `${this.apiTvShows}?`,{
          params: {
          api_key: this.idApi,
          query: this.search
        }
      })
      .then(
        (response) => {
          this.series = response.data.results.slice(0,20);
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
          const newArrayAction = response.data.results.slice(0,10).filter(
            (element) => {
              return element.genre_ids[0] == 28;
            }
          )
        this.action = newArrayAction;
        }
      ),
      axios.get( `${this.apiTopRated}?`,{
          params: {
          api_key: this.idApi,
          languages: "=it-IT",
        }
      })
      .then(
        (response) => {
          this.topRateds = response.data.results.slice(0,6);
          const newArray = response.data.results.slice(0,18).filter(
            (element) => {
              return element.genre_ids[0] == 18;
            }
          )
          this.soap = newArray;
        }
      ),
    ])
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
</style>
