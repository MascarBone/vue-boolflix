<template>
    <div>
        <ul>
            <li v-for="element in list" :key="element.id">
                <p>Titolo -  {{element.title}}</p>
                <p>Tittolo originale - {{element['original_title']}} </p>
                <p>Lingua - {{element['original_language']}}</p>
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
    }
}
</script>

<style>

</style>