<template>
  <section></section>
</template>

<script>
import axios from "axios";
export default {
  name: "Main",
  props: {
    infoFilm: String,
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
      .then(function (response) {
        console.log(response);
      });
  },
};
</script>

<style>
</style>