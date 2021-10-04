<template>
  <div>
      
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Credits',

    props: {
        movieID: Number,
        apikey: String,
    },

    data: function() {
        return {
            linkAPICredit: 'https://api.themoviedb.org/3/',
        }
    },

    created: function() {
            const array = [];
            axios.get(this.linkAPICredit + 'movie/' + this.movieID + '/credits', {
                params : {
                    api_key: this.apikey,
                }
            })
            .then((repsonse) => {
                // console.log(repsonse.data.cast);
                for (const element of repsonse.data.cast)
                {
                    
                    console.log(element);
                    array.push(element.name);
                }
                
                console.log(array);

            });
    
    },
}
</script>

<style>

</style>