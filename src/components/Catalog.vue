<template>
    <div class="box-list">
        <div>
            <h2>Movies</h2>
            <ul>
                <li v-for="element in moviesList" :key="element.id">
                    <p>Titolo -  {{element.title}}</p>
                    <p>Tittolo originale - {{element['original_title']}} </p>
                    <p>
                        <span>Lingua - </span>

                        <img v-if="languageIT(element['original_language'])" src="../assets/flag_it.svg" alt="">
                        <img v-else-if="languageGB(element['original_language'])" src="../assets/flag_gb.svg" alt="">
                        <span v-else> {{element['original_language']}} </span>
                    </p>
                    <p>Voto - {{element['vote_average']}}</p> 
                </li>
            </ul>
        </div>
        <div>
            <h2>Series</h2>
            <ul>
                <li v-for="element in seriesList" :key="element.id">
                    <p>Tittolo - {{element['original_name']}} </p>
                    <p>
                        <span>Lingua - </span>

                        <img v-if="languageIT(element['original_language'])" src="../assets/flag_it.svg" alt="">
                        <img v-else-if="languageGB(element['original_language'])" src="../assets/flag_gb.svg" alt="">
                        <span v-else> {{element['original_language']}} </span>
                    </p>
                    <p>Voto - {{element['vote_average']}}</p> 
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Catalog',

    props: {
        moviesList: Array,
        seriesList: Array,
    },
    
    methods: {
        languageIT(el) {
            return el.includes('it');
        },

        languageGB(el) {           
            return el.includes('en');
        },
    },
}
</script>

<style scoped lang="scss">
    .box-list {
        display: flex;
    }
    p {
        img {
            width: 50px;
            vertical-align: middle;
        }
    }
</style>