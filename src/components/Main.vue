<template>
  <section class="cards">
    <!-- ciclo su array che è arrivato dalla App -->
    <h2>FILMS</h2>
    <ul>
      <li v-for="(film, index) in allFilms" :key="index">
            <filmCard :info="film"/>
      </li>
    </ul>
   <h2>SERIE TV</h2>
    <ul>
      <li v-for="(serie, index) in allSeriesTv" :key="index">
            <filmCard :infoTV="serie"/>
      </li>
    </ul>
      <!-- creo prop per madare a filmCard info sui film, (un film - un oggetto con i dati) -->
  </section>
</template>

<script>
import filmCard from './filmCard.vue';
export default {
  name: "Main",
   components: {
    filmCard,
  },
  props: {
    //  è arrivato dalla App
    allFilms: Array,
    allSeriesTv: Array
  },
};
</script>

<style lang="scss">
.cards{
    ul{
      list-style: none;
    }
}
</style>