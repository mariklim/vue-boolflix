<template>
  <section>
    <div class="cards">
      <!-- ciclo su array che è arrivato dalla App -->
      <h2>{{ allFilms == 0 ? "" : "Film" }}</h2>
      <ul>
        <li v-for="(film, index) in allFilms" :key="index">
          <filmCard :info="film" />
        </li>
      </ul>
    </div>

    <div class="cards">
      <h2>{{ allSeriesTv == 0 ? "" : "Serie TV" }}</h2>
      <ul>
        <li v-for="(serie, index) in allSeriesTv" :key="index">
          <filmCard :info="serie" />
        </li>
      </ul>
      <!-- creo prop :info per madare a filmCard info sui film, (un film - un oggetto con i dati) -->
    </div>
  </section>
</template>

<script>
import filmCard from "./filmCard.vue";
export default {
  name: "Main",
  components: {
    filmCard,
  },
  props: {
    //  è arrivato dalla App
    allFilms: Array,
    allSeriesTv: Array,
  },
};
</script>

<style lang="scss">
@import "../assets/style/common";
section {
  margin-top: 4.375rem;
  height: calc(100vh - 70px);
  overflow-y: scroll;
  scroll-behavior: smooth;
}
.cards {
    h2{
      padding: .625rem 3.125rem;
      color: rgba(255, 255, 255, 0.911);
      font-size: 1.875rem;
    }
  ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    margin: 1.875rem 0;
    li {
      width: calc(100% / 7);
    }
  }
}
</style>