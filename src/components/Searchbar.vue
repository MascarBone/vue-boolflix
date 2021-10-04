<template>
    <div class="wrapper">
        <div class="container">
            <div class="row">
                <div class="col flex-grow-1">
                    <img src="../assets/zappingflix_logo.png" alt="">
                </div>
                <form class="col flex-grow-0">
                    <input type="text" v-model.trim="needle">
                    <button @click.prevent="$emit('search',needle)" type="submit">Cerca</button>
                </form> 
            </div>
            
        </div>
           
     </div>
</template>

<script>

export default {
    name: 'Searchbar',

    data: function() {
        return {
            needle: '',

        }
    },

    methods: {
        
    },
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .wrapper {
        background-color: $bg-dark;
    }
    .row {
        padding: 20px 0;
    }
    form {
        display: flex;
        align-items: flex-end;
    }

</style>