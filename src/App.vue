<template>
  <div id="app">
    <HeaderBoolflix @search="fetchData" />
    <!-- <HeaderBoolflix @search="fetchData(userResearch)" /> cosi non trova la query-->
    <MainBoolflix />

  </div>
</template>

<script>
// 63aa7c2cb6c1863a7e65fcebb3851670 chaive api
// https://api.themoviedb.org/3/movie/550?api_key=63aa7c2cb6c1863a7e65fcebb3851670 

import axios from 'axios'
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
      urlApi: 'https://api.themoviedb.org/3',
      keyApi: '63aa7c2cb6c1863a7e65fcebb3851670',
      arrFilms: [],
    }
  },
    // axios(`${this.urlApi}/search/${type}`,
  methods:{
    fetchData(userResearch){
      
      if (userResearch !== ''){ 
        axios(`${this.urlApi}/search/movie`, {
        params:{
          api_key: this.keyApi,
          language: 'it-IT',
          query: userResearch,
        },
      })
        .then((response) => console.log(response));
      }
      // fetchDataFilm();
      // fetchDataSerie()
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
