<template>
  <div id="app">
    <Searchbar @search="searchAPI"/>

    <Catalog :moviesList="movies" :seriesList="series" :apikey="codeApiKey"/>

  </div>
</template>

<script>
import axios from 'axios';

import Searchbar from './components/Searchbar.vue';
import Catalog from './components/Catalog.vue';

export default {
  name: 'App',
  components: {
    Searchbar,
    Catalog,
  },

  data: function() {
    return {
      movies : [],
      series : [],

      codeApiKey: '4b29211095001d1a2e8e6ee5ce71ec04',
      linkAPIMovies : 'https://api.themoviedb.org/3/search/movie',
      linkAPITvseries : 'https://api.themoviedb.org/3/search/tv',
    }
  },

  methods: {
    searchAPI(needleQuery) {
        console.log(needleQuery);

        // axios.get('https://api.themoviedb.org/3/search/movie?api_key=4b29211095001d1a2e8e6ee5ce71ec04&query=' + needleQuery)
        axios.get(this.linkAPIMovies, {
          params : {            
            api_key: this.codeApiKey ,
            query: needleQuery,
          }
        })
        .then((response) => {
            console.log(response.data.results);

            this.movies = [...response.data.results];

            console.log(this.movies);
        })
        .catch((error) => {
          console.log(error);
        });

        axios.get(this.linkAPITvseries, {
          params : {            
            'api_key': this.codeApiKey ,
            query: needleQuery,
          }
        })
        .then((response) => {
            console.log(response.data.results);

            this.series = [...response.data.results]

            console.log(this.series);
        })
        .catch((error) => {
          console.log(error);
        });
    }
  },
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
