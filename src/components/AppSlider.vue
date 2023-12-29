<template lang="">
    <h3>
        AppSlider
    </h3>
    
    <SingleSlide class="card" v-for="(movie, index) in moviesList"
        :key="moviesList[index].id"
        :index="index"
        :visibleSlide = "visibleSlide"
        :title = "moviesList[index].original_title"
        :imgSource = "`http://image.tmdb.org/t/p/w200/${moviesList[index].poster_path}`"
    />
    <button class="prev" @click="prevSlide">Prev</button>
    <button class="next" @click="nextSlide">Next</button>
</template>

<script>
import axios from 'axios';

import SingleSlide from './SingleSlide.vue';

export default {
    name: "AppSlider",

    components: {
        SingleSlide
    },

    data() {
        return {
            moviesList: [],

            visibleSlide: 0,
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
        },
        
        nextSlide() {
            if (this.visibleSlide >= this.moviesList.length - 1) {
                this.visibleSlide = 0;
            } else {
                this.visibleSlide ++;
            };
        },

        prevSlide() {
            if (this.visibleSlide <= 0) {
                this.visibleSlide = this.moviesList.length - 1;
            } else {
                this.visibleSlide --;
            };
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