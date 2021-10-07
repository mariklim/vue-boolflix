<template>
  
    <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->
    <div class="card">
      <!-- Titolo categotia -->
      <!-- <h2 v-if="info.original_title">FILM</h2>
      <h2 v-else>SERIE TV</h2> -->
      <!-- /Titolo categotia -->

      <!-- Info sui Film e Serie -->
      <!-- <h2 v-if="info.original_title">
        Titolo originale: {{ info.original_title }}
      </h2>
      <h2 v-else>Titolo originale: {{ info.original_name }}</h2>

      <h2 v-if="info.title">Titolo: {{ info.title }}</h2>
      <h2 v-else>Titolo: {{ info.name }}</h2> -->
      <!-- /Info sui Film e Serie -->

      <!-- Voto -->
      <!-- <span class="stars" v-for="n in votoCalc" :key="n">
        <i class="fas fa-star"></i>
      </span>

      <span class="starsEmpty" v-for="n in 5 - votoCalc" :key="n">
        <i class="far fa-star"></i>
      </span> -->
      <!-- /Voto -->
      <!--Lingua e Poster -->
      <img
        :src="`https://image.tmdb.org/t/p/w200/${info.poster_path}`"
        alt=""/>
         <h4>Lingua:</h4>
      <lang-flag :iso="info.original_language" />
      <!--/Lingua e Poster -->
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
  color: rgb(255, 255, 255);
  & i {
    display: inline-block;
    color: gold;
  }
}
</style>