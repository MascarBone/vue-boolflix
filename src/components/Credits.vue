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
        // console.log(this.type, this.index);
    // }
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
                        this.listNames.push(element.name);
                        continue;
                    }
                    else
                    {
                        break;
                    }
                }
                
                console.log(this.listNames);
            });
    
    },
}
</script>

<style>

</style>