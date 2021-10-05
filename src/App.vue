<template>
  <div id="app">
    <Header @search="searchFilm" />
    <Main :allFilms="allFilms" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
		return {
			inputText:"",
      allFilms: [],
		}
	},
  methods: {
    //Al evento click avvio funzione "searchFilm", che "salva" il valore della input (quello che inserisce utente nella serachbar)
		searchFilm(text) {
			this.inputText = text;
      console.log(this.inputText);
      //al click si avvia la chiamata ad API
      axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "49c4ea87380c56e0d9c16d3ec78d73d7",
          query: this.inputText,
          language: "it-IT",
        },
      })
      .then((response) => {
        console.log(response.data.results);
        this.allFilms = response.data.results;
        console.log(this.allFilms);
      });
		}
	},
}
</script>

<style lang="scss">
</style>
