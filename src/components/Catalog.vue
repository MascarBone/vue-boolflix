<template>
    <div class="container">
        <div class="row mb-5 justify-content-center">
            <h2 class="col-12">Movies</h2>
            <div v-for="element in moviesList" :key="element.id" class="col-3">
                <Card :card="element"/>
            </div>
        </div>
        <div class="row justify-content-center">
            <h2 class="col-12">Series</h2>
            <div v-for="element in seriesList" :key="element.id" class="col-3">
                <Card :card="element"/>
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
    },
    
    
}
</script>

<style scoped lang="scss">

</style>