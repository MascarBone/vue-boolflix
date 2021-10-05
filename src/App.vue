<template>
  <div id="app">
    <Searchbar @search="searchAPI"/>

    <!-- <Catalog :moviesList="movies" :seriesList="series" :apikey="apikey"/> -->
    <Catalog :mediaList="media" :apikey="apikey"/>


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
      media : [],

      apikey: '4b29211095001d1a2e8e6ee5ce71ec04',
      APIMovies: 'https://api.themoviedb.org/3/search/movie',
      APITvseries: 'https://api.themoviedb.org/3/search/tv',
      APIMulti: 'https://api.themoviedb.org/3/search/multi',

    }
  },

  methods: {
    searchAPI(needleQuery) {
        console.log(needleQuery);

        // axios.get(this.APIMovies, {
        //   params : {            
        //     api_key: this.apikey ,
        //     query: needleQuery,
        //   }
        // })
        // .then((response) => {
        //     console.log(response.data.results);

        //     this.movies = [...response.data.results];

        //     console.log(this.movies);
        // })
        // .catch((error) => {
        //   console.log(error);
        // });

        // axios.get(this.APITvseries, {
        //   params : {            
        //     'api_key': this.apikey ,
        //     query: needleQuery,
        //   }
        // })
        // .then((response) => {
        //     console.log(response.data.results);

        //     this.series = [...response.data.results]

        //     console.log(this.series);
        // })
        // .catch((error) => {
        //   console.log(error);
        // });

        // this.eventoProva(needleQuery);
        axios.get(this.APIMulti , {
          params: {
            api_key: this.apikey,
            query: needleQuery,
          }
        })
        .then((response) => {
          console.log('eventoMultiSearch');
          console.log(response);
          this.media = [...response.data.results];
          console.log(this.media);
        })
    },
   
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
