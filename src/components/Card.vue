<template>
  <div>
        <div v-if="card.backdrop_path">
            <img :src="'https://image.tmdb.org/t/p/' + 'w300/' + card.backdrop_path" alt="">
        </div>
        <div v-else class="img-else">
            <img src="https://c.tenor.com/5JunKCV2DEIAAAAC/error404-404.gif" alt="">
        </div>
        <p>Titolo -  {{ card.title ? card.title : card.name}}</p>
        <p>Tittolo originale - {{ card.original_title ? card.original_title : card.original_name}}</p>
        <div class="language-box">
            <img v-if="languageIT(card.original_language)" src="../assets/flag_it.svg" alt="">
            <img v-else-if="languageGB(card.original_language)" src="../assets/flag_gb.svg" alt="">
            <span v-else>Lingua - {{card.original_language}} </span>
        </div>
        <p>Voto - {{card.vote_average}}</p>
        <div>
            <span v-for="n in 5" :key="n">
                <i :class="n <= stars ? 'fas fa-star' : 'far fa-star'"></i>
            </span>
        </div>
  </div>
</template>

<script>
export default {
    name: 'Card',

    props: {
        card: Object,
    },

    computed: {
        stars: function() {
            return Math.ceil(this.card.vote_average / 2);
        }
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
@import '~@fortawesome/fontawesome-free/css/all.css';

    .img-else {
        width: 300px;
        
        img {
            width: 100%;
        }
    }

    .language-box {
        img {
            width: 50px;
            vertical-align: middle;
        }
    }
</style>