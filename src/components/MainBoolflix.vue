<template>
  <main>
    <div class="container">
      <card-film 
      v-for="film in arrFilms" 
      :key="film.id" 
      :card-data="film" 
      />
    </div>
  </main>
</template>

<script>
import CardFilm from "./CardFilm.vue";
export default {
  name: "MainBoolflix",
  components: {
    CardFilm,
  },
  props: {
    arrFilms: Array,
    arrSeries: Array,
  },
};
</script>

<style lang="scss" scoped>
</style>
