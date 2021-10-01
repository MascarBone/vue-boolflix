<template>
  <div>
      <form>
            <input type="text" v-model="needle">
            <button @click.prevent="$emit('search',needle)" type="submit">Cerca</button>

      </form>      
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

<style>

</style>