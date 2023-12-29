<template lang="">
    <h3>
        AppSlider
    </h3>
</template>

<script>
import axios from 'axios';

export default {
    name: "AppSlider",

    data() {
        return {
            moviesList: [],
        }
    },

    methods: {

        getMovieDetails() {
            // CHIAMATA AXIOS per ottenere i dettagli del film
            axios.get('https://api.themoviedb.org/3/movie/', {
                params: {
                    movie_id: "547205",
                    api_key: "035eedbe7389d3160c097087910908d0",
                }
            })
            .then((response) => {
                console.log(response.data);
                this.moviesList.push(response.data);
            })
            .catch(function (error) {
                console.log(error);
            });
        }  
    },

    created() {
        console.log(this.moviesList);
        this.getMovieDetails
    },
}
</script>
<style lang="">
    
</style>