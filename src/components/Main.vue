<template>
  <section class="cards">
    <!-- ciclo su array che è arrivato dalla App -->
    <ul>
      <li v-for="(film, index) in allFilms" :key="index">
            <filmCard :info="film"/>
      </li>
    </ul>
    <ul>
      <li v-for="(serie, index) in allSeriesTv" :key="index">
            <filmCard :info="serie"/>
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
@import "../assets/style/common";
section{
  margin-top: 4.375rem;
  height: calc(100vh - 70px);
  overflow-y: scroll;
  scroll-behavior: smooth;
}
.cards{
    ul{
      list-style: none;
    }
}
</style>