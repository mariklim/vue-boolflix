<template>
  <section class="cards">
    <!-- ciclo su array che è arrivato dalla App -->
    <div v-for="(film, index) in allFilms" :key="index">
      
      <!-- creo prop per madare a filmCard info sui film, (un film - un oggetto con i dati) -->
    <filmCard :info="film"/>
    </div>
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
}
</style>