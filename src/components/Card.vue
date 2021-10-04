<template>
  <div>
        <div class="poster">
            <div v-if="card.poster_path" class="poster_img">
                <img :src="'https://image.tmdb.org/t/p/' + 'w342/' + card.poster_path" alt="">
            </div>
            <div v-else class="poster_img">
                <img src="https://c.tenor.com/5JunKCV2DEIAAAAC/error404-404.gif" alt="">
            </div>

            <div class="poster_text">
                <p>Titolo -  {{ card.title ? card.title : card.name}}</p>
                <p>Tittolo originale - {{ card.original_title ? card.original_title : card.original_name}}</p>
                <div class="language-box">
                    <img v-if="languageIT(card.original_language)" src="../assets/flag_it.svg" alt="">
                    <img v-else-if="languageGB(card.original_language)" src="../assets/flag_gb.svg" alt="">
                    <span v-else>Lingua - {{card.original_language}} </span>
                </div>
                <div>
                    <span v-for="n in 5" :key="n">
                        <i :class="n <= stars ? 'fas fa-star' : 'far fa-star'"></i>
                    </span>
                </div>

                <Credits :type="creditType" :index="card.id" :apikey="apikey"/>

                <p>Overview - {{card.overview}}</p>
            </div>
        </div>
        
        

        
  </div>
</template>

<script>
import Credits from './Credits.vue'

export default {
    name: 'Card',

    components: {
        Credits,
    },

    props: {
        card: Object,
        apikey: String,
        creditType: String,
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
    
    created: function() {
        console.log(this.creditType);
    },
}

</script>

<style scoped lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';

    *{
        text-align: start;

    }
    .poster {
        position: relative;
        background-color: black;
    }
    .poster_img {
        z-index: 0;
        width: 100%;

        img {
            width: 100%;
        }
    }
    .poster_text {
        color: white;
        padding: 20px;
        position: absolute;
        top: 0;
        z-index: -1;

        i {
            color: goldenrod;
        }
        > * {
            margin-bottom: 8px;
        }
    }

    .language-box {
        img {
            width: 50px;
            vertical-align: middle;
        }
    }


    .poster:hover .poster_img{
        opacity: 0;
    }
    .poster:hover .poster_text{
        z-index: 1;
    }
</style>