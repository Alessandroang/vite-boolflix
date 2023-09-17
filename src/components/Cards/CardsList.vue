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
  <h2>
    {{ title }}
  </h2>

  <ul>
    <li>
      {{ movie.name }}
      {{ movie.language }}
      {{ movie.original_title }}
      {{ movie.vote }}
    </li>
  </ul>

  <CardDetail v-for="movie in store.movies" :key="movie.id" />
</template>

<style lang="scss" scoped></style>
