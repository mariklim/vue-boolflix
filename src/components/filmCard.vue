<template>
  <div>
    <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->
    <div class="card">
        <h2 v-if="info.original_title">
            Titolo originale: {{ info.original_title }}
        </h2>
        <h2 v-else>Titolo originale: {{ info.original_name }}</h2>
        <h2 v-if="info.title">Titolo: {{ info.title }}</h2>
        <h2 v-else>Titolo: {{ info.name }}</h2>
        <span class="stars" v-for="n in votoCalc" :key="n">
            <i class="fas fa-star"></i>
            </span>
        <h4>Lingua:</h4>
        <lang-flag :iso="info.original_language" />
        <img
            :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`"
            alt=""
        />
    </div>
  </div>
</template> 

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "filmCard",
  components: {
    LangFlag,
  },
  // è arrivato dalla Main
  props: {
    info: Object,
  },
  data() {
    return {
      votoCalc: parseInt(this.info.vote_average / 2),
    };
  },
  
};
</script>


<style lang="scss">
@import "../assets/style/common";
.card {
  color: rgb(15, 13, 13);
  border: 1px solid gray;
    & i{
        display: inline-block;
        color: gold;
    }
}
</style>