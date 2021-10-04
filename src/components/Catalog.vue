<template>
<div class="wrapper">
    <div class="container">
        <div class="row mb-5 justify-content-center">
            <h2 class="col-12">Movies</h2>
            <div v-for="element in moviesList" :key="element.id" class="col-3">
                <Card :creditType="'movie'" :card="element" :apikey="apikey"/>
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
import Card from './Card.vue';

export default {
    name: 'Catalog',

    components: {
        Card,
    },

    props: {
        moviesList: Array,
        seriesList: Array,
        apikey: String,
    },
    
    // created: {

    // }
    
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

.wrapper {
    background-color: $bg-page;
}
</style>