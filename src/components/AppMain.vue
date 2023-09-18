<script>
import CardsList from "./Cards/CardsList.vue";

export default {
  data() {
    return {
      title: "App Main",
    };
  },
  components: {
    CardsList,
  },
};
</script>
<template>
  <main class="container mt-5">
    <CardsList />
  </main>
</template>

<style lang="scss" scoped></style>
