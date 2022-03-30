<template>
  <div id="app">
    <HeaderBoolflix />
    <MainBoolflix />

  </div>
</template>

<script>
// 63aa7c2cb6c1863a7e65fcebb3851670 chaive api
// https://api.themoviedb.org/3/movie/550?api_key=63aa7c2cb6c1863a7e65fcebb3851670 

// import axios from 'axios'
import HeaderBoolflix from './components/HeaderBoolflix.vue'
import MainBoolflix from './components/MainBoolflix.vue'


export default {
  name: 'App',
  components: {
    HeaderBoolflix,
    MainBoolflix,
  },
  data(){
    return{
      language: 'it-IT',
      arrFilms: [],
    }
  }
}

</script>

<style lang="scss">
@import "./assets/styles/style.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
