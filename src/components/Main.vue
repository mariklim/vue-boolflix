<template>
  <section>
        
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "Main",
  props: {
    infoFilm: String,
  },
   data() {
    return {
      allFilms:[],
    };
  },
  created() {
    axios
      .get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '49c4ea87380c56e0d9c16d3ec78d73d7',
          query: 'Ritorno al futuro',
          language: 'it-IT',
        },
      })
      .then((response) => {
        console.log(response.data.results);
        this.allFilms = response.data.results;
        console.log(this.allFilms);
      });
  },
};
</script>

<style>
</style>