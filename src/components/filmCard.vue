<template>
  
    <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->
    <div class="card">  
      <!--Poster -->
      <div class="card-img">
        <img v-if="info.poster_path == null" :src="require(`../assets/image/netflix.jpg`)" alt="netflix">
         <img v-else
        :src="`https://image.tmdb.org/t/p/w200/${info.poster_path}`" alt=""/>
      </div>
        <div class="info-card">
         <h3 v-if="info.original_title">
        Titolo originale: {{ info.original_title }}
      </h3>
      <h3 v-else>Titolo originale: {{ info.original_name }}</h3>

      <h3 v-if="info.title">Titolo: {{ info.title }}</h3>
      <h3 v-else>Titolo: {{ info.name }}</h3>
      <!-- /Info sui Film e Serie -->

      <!-- Voto -->
      <span class="stars" v-for="n in votoCalc" :key="n">
        <i class="fas fa-star"></i>
      </span>

      <span class="starsEmpty" v-for="numero in 5 - votoCalc" :key="numero">
        <i class="far fa-star"></i>
      </span>
      <!-- /Voto -->

      <h4>Lingua:</h4>
      <lang-flag :iso="info.original_language" />

      </div>
      <!-- Info sui Film e Serie -->
      
      <!--/Poster -->
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
  .card-img{
    width: 11.25rem;
    height: 15.625rem;
    overflow: hidden;
     img{
       width: 100%;
     }
  }
  .info-card{
    font-size: .9375rem;
    border: 1px solid white;
    width: 11.25rem;
    height: 15.625rem;
    padding: 1.25rem;
  }
}
.card-img:hover .info-card{
background-color: magenta;
}

</style>