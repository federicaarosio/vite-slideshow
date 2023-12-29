<template lang="">
    <h3>
        AppSlider
    </h3>
    <div class="card" v-for="(movie, index) in moviesList" :key="moviesList[index].id">
        <p>{{moviesList[index].original_title}}</p>
        <img :src="`http://image.tmdb.org/t/p/w200/${moviesList[index].poster_path}`" alt="">
    </div>
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

        getMovieDetails(movie_id) {
            // Chiamata axios per ottenere i dettagli del film. Passo l'id del film come argomento
            axios.get(`https://api.themoviedb.org/3/movie/${movie_id}`, {
                params: {
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
        this.getMovieDetails("120");
        this.getMovieDetails("9361");
        this.getMovieDetails("50014");
        this.getMovieDetails("78");
        this.getMovieDetails("424");
    },
}
</script>
<style lang="">
    
</style>