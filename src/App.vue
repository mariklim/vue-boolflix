<template>
  <div id="app">
    <!-- App "ascolta" un evento click del bottone della serjbar e quando "lo sente" fa partire il metodo "searchFilm" -->
    <Header @search="searchFilm" />

    <!-- passo dati della array nel componente Main -->
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
      //creo variabli vuoti dove salvare dati in arrivo: della input, e da API
			inputText:"",
      allFilms: [],
		}
	},
  methods: {
    //Al evento click avvio funzione "searchFilm", che "salva" il valore della input (quello che inserisce utente nella serachbar)
		searchFilm(text) {
			this.inputText = text;
      console.log(this.inputText);
      //al click si avvia la chiamata ad API e cambia il contenuto del Array allFilms secondo al valore della Query (che prende valore della input, quindi è dinamica, non serve fare un ulteriore filtro)
      axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "49c4ea87380c56e0d9c16d3ec78d73d7",
          
          //faccio queri dinamica, il suo valore è quello che scrive utente nel input della searchbar
          query: this.inputText,
          language: "it-IT",
        },
      })
      .then((response) => {
        console.log(response.data.results);
        //assegno direttamente all array tutto il contenuto da API, non serve fare il filtro
        this.allFilms = response.data.results;
        console.log(this.allFilms);
      });
		}
	},
}
</script>

<style lang="scss">
</style>
