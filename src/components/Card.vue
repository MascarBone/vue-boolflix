<template>
  <div>
        <p>Titolo -  {{ card.title ? card.title : card.name}}</p>
        <p>Tittolo originale - {{ card.original_title ? card.original_title : card.original_name}}</p>
        <div class="language-box">
            <img v-if="languageIT(card.original_language)" src="../assets/flag_it.svg" alt="">
            <img v-else-if="languageGB(card.original_language)" src="../assets/flag_gb.svg" alt="">
            <span v-else>Lingua - {{card.original_language}} </span>
        </div>
        <p>Voto - {{card['vote_average']}}</p> 
  </div>
</template>

<script>
export default {
    name: 'Card',

    props: {
        card: Object,
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

    .language-box {
        img {
            width: 50px;
            vertical-align: middle;
        }
    }
</style>