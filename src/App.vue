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
          const moviesData = response.data.results.map((movie) => {
            const id = movie.id;
            const name = movie.title;
            const original_title = movie.original_title;
            const original_language = movie.original_language;
            const vote_average = movie.vote_average;

            return {
              id,
              name,
              original_title,
              original_language,
              vote_average,
            };
          });
          store.movies = moviesData;
        });
    },

    fetchTvSeries(queryString) {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            query: queryString,
            api_key: "e39a0d6afdf457f94ef22d6ef6402331",
          },
        })
        .then((response) => {
          const tvSeriesData = response.data.results.map((tvSeries) => {
            const id = tvSeries.id;
            const title = tvSeries.name;
            const original_title = tvSeries.original_name;
            const original_language = tvSeries.original_language;
            const vote_average = tvSeries.vote_average;

            return {
              id,
              name,
              original_title,
              original_language,
              vote,
            };
          });
          store.tvSeries = tvSeriesData;
        });
    },
    handlSearch(queryString) {
      console.log(queryString);
      if (!queryString) return;
      this.fetchMovies(queryString);
      this.fetchTvSeries(queryString);
    },
  },
};
</script>
<template>
  <AppHeader @startsearch="handlSearch" />

  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/style.scss" as *;
</style>
