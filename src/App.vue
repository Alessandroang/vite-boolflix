<script>
import { store } from "./data/store";

import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  data() {
    return {
      movies: [],
    };
  },

  components: { AppHeader, AppMain },

  methods: {
    fetchMovies(queryString) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            query: queryString,
            api_key: "e39a0d6afdf457f94ef22d6ef6402331",
          },
        })
        .then((response) => {
          store.movies = response.data.results.map((movie) => {
            const {
              id,
              title,
              original_title,
              original_language,
              vote_average,
            } = movie;
            return {
              id,
              name: title,
              original_title,
              language: original_language,
              vote: vote_average,
            };
          });
        });
    },

    handleStartSearch() {
      console.log("il form di ricerca è stato inviato");
    },
  },

  created() {
    // this.fetchMovies();
  },
};
</script>
<template>
  <AppHeader @start-search="fetchMovies" />
  <!-- 
  <ul>
    <li v-for="movie in store.movies" :key="movie.id">
      {{ movie.name }}
      {{ movie.language }}
      {{ movie.original_title }}
      {{ movie.vote }}
    </li>
  </ul> -->
  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/style.scss" as *;
</style>
