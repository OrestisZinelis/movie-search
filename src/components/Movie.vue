<template>
  <div class="movie">
    <div class="movie__title">{{ movie.Title }}</div>
    <div>
      <img width="200" height="300px" :alt="altText" :src="movie.Poster" />
    </div>
    <p>{{ movie.Year }}</p>
  </div>
</template>

<script>
import { computed } from "@vue/composition-api";

export default {
  name: "Movie",
  props: ["movie"],
  setup({ movie }) {
    const altText = computed(() => `The movie titled: ${movie.Title}`);

    return { altText };
  },
};
</script>
