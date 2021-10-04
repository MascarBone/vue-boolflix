<template>
    <div>
        <span v-for="(element, index) in listNames" :key="index">
            {{element}};
        </span>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Credits',

    props: {
        type: String,
        index: Number,
        apikey: String,
    },

    data: function() {
        return {
            linkAPICredit: 'https://api.themoviedb.org/3/',
            listNames: [],
        }
    },

    created: function() {
        // const array = [];
            axios.get(this.linkAPICredit + this.type + '/' + this.index + '/credits', {
                params : {
                    api_key: this.apikey,
                }
            })
            .then((repsonse) => {
                // console.log(repsonse.data.cast);
                for (const element of repsonse.data.cast)
                {                    
                    if(this.listNames.length < 5)
                    {      
                        this.listNames.push(this.fullname(element.name.split(' ')));                  
                        // this.listNames.push(element.name);
                        // array.push(this.fullname(element.name.split(' ')));
                        continue;
                    }
                    else
                    {
                        break;
                    }
                }
                // console.log(array);
                // console.log(this.listNames);

            });
    
    },

    /**
     * Funzione che ritorna solo il primo e l'ultimo elemento di un array
     */
    methods: {
        fullname: function(array) {
            return [array[0],array[array.length-1]].join(' ');
        }
    },
}
</script>

<style>

</style>