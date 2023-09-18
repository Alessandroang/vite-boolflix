<script>
import { store } from "../../data/store";

import CardDetail from "./CardDetail.vue";

export default {
  data() {
    return {
      title: "CardsList",
      store,
    };
  },
  components: { CardDetail },
};
</script>
<template>
  <section>
    <h2>Movies</h2>
    {{ store.movies.length }}
    <CardDetail
      v-for="movie in store.movies"
      :key="movie.id"
      :cardInfo="movie"
    />
  </section>
  <!-- <section>
    <h2>Tv Series</h2>
    {{ store.tvSeries.length }}
    <CardDetail
      v-for="tvSeries in store.tvSeries"
      :key="tvSeries.id"
      :cardInfo="tvSeries"
    />
  </section> -->
</template>

<style lang="scss" scoped></style>
