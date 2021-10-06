<template>
  <section class="cards">
    <!-- ciclo su array che è arrivato dalla App -->
    <ul>
      <li v-for="(film, index) in allFilms" :key="index">
            <filmCard :info="film"/>
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
  },
};
</script>

<style lang="scss">
.cards{
  display: flex;
  flex-wrap: wrap;
    ul{
      list-style: none;
    }
}
</style>