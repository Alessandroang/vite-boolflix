<script>
export default {
  props: {
    cardInfo: Object,
  },

  computed: {
    hasFlag() {
      const allowedFlags = ["en", "it"];
      return allowedFlags.includes(this.cardInfo.language);
    },

    flagSrc() {
      const flagUrl = new URL(
        "../../assets/img/${this.cardInfo.language}.png",
        import.meta.url
      );
      return flagUrl.href;
    },
  },
};
</script>
<template>
  <div class="card">
    <div class="card-body">
      <ul>
        <li>{{ cardInfo.name }}</li>
        <li>{{ cardInfo.original_title }}</li>
        <!-- <li v-if="hasFlag">
          <img :src="flagSrc" :alt="cardInfo.name" />
        </li> -->
        <li>{{ cardInfo.original_language }}</li>
        <li>{{ cardInfo.vote_average }}</li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
