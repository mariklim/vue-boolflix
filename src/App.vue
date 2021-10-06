<template>
  <div id="app">
    <!-- App "ascolta" un evento click del bottone della serjbar e quando "lo sente" fa partire il metodo "searchFilm" -->
    <Header @search="searchFilm" />

    <!-- passo dati delle array nel componente Main -->
    <Main 
    :allFilms="allFilms" 
    :allSeriesTv="allSeriesTv"
    
    />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      //creo variabli vuoti dove salvare dati in arrivo: della input, e da API
      allFilms: [],
      allSeriesTv: [],
    };
  },
  methods: {
    //Al evento click avvio funzione "searchFilm", che "salva" il valore della input (quello che inserisce utente nella serachbar)
    searchFilm(inputText) {
      console.log(inputText);
      //al click si avvia la chiamata ad API e cambia il contenuto del Array allFilms secondo al valore della Query (che prende valore della input, quindi è dinamica, non serve fare un ulteriore filtro)

        // API FILMS
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "49c4ea87380c56e0d9c16d3ec78d73d7",

            //faccio query dinamica, il suo valore è quello che scrive utente nel input della searchbar
            query: inputText,
            language: "it-IT",
          },
        })
        
        .then((response) => {
          this.allFilms = response.data.results;
          console.log(this.allFilms)
        
        });

        // API SERIE TV
        axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "49c4ea87380c56e0d9c16d3ec78d73d7",

            //faccio query dinamica, il suo valore è quello che scrive utente nel input della searchbar
            query: inputText,
            language: "it-IT",
          },
        })

        .then((response) => {
          this.allSeriesTv = response.data.results;
          console.log(  this.allSeriesTv)
        
        });
        
    },
  },
};
</script>

<style lang="scss">
</style>
