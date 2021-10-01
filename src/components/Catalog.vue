<template>
    <div>
        <ul>
            <li v-for="element in list" :key="element.id">
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
</template>

<script>
export default {
    name: 'Catalog',

    props: {
        list: Array,
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
    p {
        img {
            width: 50px;
            vertical-align: middle;
        }
    }
</style>