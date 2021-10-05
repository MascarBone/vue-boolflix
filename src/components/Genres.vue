<template>
  <div>
      <form @change="$emit('selection', checked.sort())">
        <div v-for="genre in genres" :key="genre.id" class="box-check">
            <input type="checkbox" :id="genre.id" :value="genre.id" v-model="checked">
            <label :for="genre.id">{{genre.name}}</label>
        </div>
      </form>
        
        <span>{{checked}}</span>
  </div>
</template>

<script>
export default {
    name: 'Genres',

    props: {
        genres: Array,
    },

    data: function() {
        return {
            checked: [],
        }
    }
}
</script>

<style scoped lang="scss">
form {
    display: flex;
    flex-wrap: wrap;
}
.box-check {
    padding: 4px 10px;
    margin: 5px 8px;
    font-size: 1.2rem;
    background-color: rgba(255, 255, 255, 0.205);

    input {
        margin-right: 5px;
        cursor: pointer;
    }
    label {
        
        cursor: pointer;
    }
}
</style>