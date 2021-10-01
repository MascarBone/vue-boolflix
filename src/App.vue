<template>
  <div id="app">
    <h1>RICERCA</h1>

    <Searchbar @search="evento"/>

    <Catalog />
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
    }
  },

  methods: {
    evento(needleQuery) {
        console.log(needleQuery);

        axios.get('https://api.themoviedb.org/3/search/movie?api_key=4b29211095001d1a2e8e6ee5ce71ec04&query=' + needleQuery)
        .then((response) => {
            console.log(response.data.results);
            // this.movies = response.data.results.slice();
            this.movies = [...response.data.results];
            console.log(this.movies);
        })
    }
  },
}
</script>

<style lang="scss">


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
