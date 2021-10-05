<template>
<div class="wrapper">
    <div class="container">
        <div class="row mb-5 justify-content-center">
            <h2 class="col-12">Movies</h2>
            <div v-for="element in moviesList" :key="element.id" class="col-3">

                <Card :genres="funzioneG(element.genre_ids, movieGenres)" :creditType="'movie'" :card="element" :apikey="apikey"/>
            </div>
        </div>
        <div class="row justify-content-center">
            <h2 class="col-12">Series</h2>
            <div v-for="element in seriesList" :key="element.id" class="col-3">
                <Card :creditType="'tv'" :card="element" :apikey="apikey"/>
            </div>
        </div>
    </div>
</div>
    
</template>

<script>
import axios from 'axios';

import Card from './Card.vue';

export default {
    name: 'Catalog',

    components: {
        Card,
    },

    data: function() {
        return {            
            movieGenres: [],
            serieGenres: [],

            APIMovieGenres: 'https://api.themoviedb.org/3/genre/movie/list',
            APISerieGenres: 'https://api.themoviedb.org/3/genre/tv/list',
        }
    },

    props: {
        moviesList: Array,
        seriesList: Array,
        apikey: String,
    },

    methods: {

        /**
         * Funzione che restituisce un array di oggetti, contente l'id del genere ed il nome del genere
         * @param {array} ids un array contenente gli di presenti nel file
         * @param {array} genres un array di oggetti, con l'id del genere ed il nome
         * @return {array} ritorna un array come genres filtrato per ids
         */
        funzioneG(ids, genres) {
            // console.log('funzioneG');
            // console.log(ids);
            // console.log(genres);
            
            // let arrayR = [];
            // return genres.filter(element => ids.includes(element.id)).map(x => x.name)

            return genres.filter(element => ids.includes(element.id));
            // console.log(arrayR);
        }        
    },
    
    /**
     * Hook che al momento che Catalog viene creato, chiama l'API per salvare i generi disponibili per movies e serie tv
     */
    created: function() {
        console.log('Created');
        axios.get(this.APIMovieGenres, {
        params: {
            api_key: this.apikey,
        }
        })
        .then((response) => {
        this.movieGenres = [...response.data.genres];
        console.log(this.movieGenres);
        });

        axios.get(this.APISerieGenres, {
        params: {
            api_key: this.apikey,
        }
        })
        .then((response) => {
        this.serieGenres = [...response.data.genres];
        console.log(this.serieGenres);
        });
    },
    
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

.wrapper {
    background-color: $bg-page;
}
</style>