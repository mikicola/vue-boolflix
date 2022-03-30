<template>
  <div id="app">
    <HeaderBoolflix @search="fetchData" />
    <!-- <HeaderBoolflix @search="fetchData(userResearch)" /> cosi non trova la query-->
    <MainBoolflix 
      :arr-films="arrFilms"
      :arr-series="arrSeries"
    />
    <!-- riga 6 7 porto gli array da app a main -->

  </div>
</template>

<script>
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
      arrSeries: []
    }
  },
    // axios(`${this.urlApi}/search/${type}`,
  methods:{
    fetchData(userResearch){
      
      if (userResearch !== ''){ 
        const objParams = {
           api_key: this.keyApi,
          language: 'it-IT',
          query: userResearch,
        };
        // ricerca film 
        axios(`${this.urlApi}/search/movie`, {
        params:{
          api_key: this.keyApi,
          language: 'it-IT',
          query: userResearch,
        },
      })
        // .then((response) => console.log(response));
        .then((response) => {this.arrFilms = response.data.results;}); //metto risultati dall'api nell'array

        // ricerca serie
        this.axiosCall( 'tv', objParams, this.arrSeries);
        
      
      }
    },
    // eslint-disable-next-line no-unused-vars
    axiosCall(type, objParams, destination){
        axios(`${this.urlApi}/search/${type}`, {
        params:{
          api_key: this.keyApi,
          language: 'it-IT',
          // eslint-disable-next-line no-undef
          query: userResearch,
        },
      })
      .then((response) => {
        if(type === 'film'){
          // se il type è film prendi questi dati dall'api 
          this.arrFilms = response.data.results.map((film) => ({
            id: film.id ,
            title: film.title,
            originalTitle: film.original_title,
            language: film.original_language,
            vote: film.vote_average,
          }))
          }else{
            // se il type è serie questi altri dati dall'api 
            this.arrSeries = response.data.results.map((series)=> ({
            id: series.id ,
            title: series.name,
            originalTitle: series.original_name,
            language: series.original_language,
            vote: series.vote_average,
        }))
          }
        }
      ) 
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
