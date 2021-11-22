<template>
  <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->
  <div class="card">
    <!-- poster -->
    <img
      v-if="info.poster_path == null"
      :src="require(`../assets/image/netflix.jpg`)"
      alt="netflix"
    />
    <img
      v-else
      :src="`https://image.tmdb.org/t/p/w200/${info.poster_path}`"
      alt=""
    />
    <!-- /poster -->
    
    <!--Info sui Film e Serie -->
    <div class="info-card">
      <p v-if="info.title">Titolo:<span><h4>{{ info.title }}</h4></span></p>
      <p v-else>Titolo: <span><h4>{{ info.name }}</h4></span></p>

      <p v-if="info.original_title">Titolo originale:<span><h4>{{ info.original_title }}</h4></span></p>
      <p v-else>Titolo originale:<span><h4> {{ info.original_name }}</h4></span></p>

      <!-- /Info sui Film e Serie -->
      <span id="lang">Lingua originale:</span>
      <lang-flag :iso="info.original_language" />


      <!-- Voto -->
      <div class="voto">
          <span class="stars" v-for="n in votoCalc" :key="n">
          <i class="fas fa-star"></i>
        </span>

        <span class="starsEmpty" v-for="numero in 5 - votoCalc" :key="numero">
          <i class="far fa-star"></i>
        </span>
      </div>
     
      <!-- /Voto -->
    </div>

    <!-- Info sui Film e Serie -->
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
    infoGenre: Object
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
  width: 200px;
  height: 300px;
  position: relative;
  color: rgb(255, 255, 255);
  transition: all 0.3s;
  transform: scale(1);

  img {
    width: 100%;
    height: 100%;
  }

  & i {
    color: gold;
  }

  .info-card {
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    font-size: 0.9375rem;
    padding: 1.25rem;
    background-color: rgba(32, 32, 32, 0.918);
    border: 1px solid rgba(66, 56, 56, 0.966);
    opacity: 0;
    transition: opacity 1s;
      h5, p{
        padding: .625rem 0;
      }
      p, #lang{
        font-size: .75rem;
        }
      #lang{
        padding-right: .625rem;
      }
      .voto{
        margin: .625rem 0;
      }
      }
  }
.card:hover .info-card {
  opacity: 1;
}
.card:hover {
  transform: scale(1.3);
  box-shadow: 6px 8px 5px -3px rgba(0, 0, 0, 0.68);
  z-index: 1;
}

</style>