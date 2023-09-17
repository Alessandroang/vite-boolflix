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
  <div class="container mt-5">
    <CardsList />
  </div>
</template>

<style lang="scss" scoped></style>
