<template>
  <section class="cards">
    <filmCard v-for="(film, index) in allFilms" :key="index" :info="film"/>
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