<template>
  <div class="card">
    <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->

    <h2>Titolo originale: {{ info.original_title }}</h2>
    <h3>Titolo: {{ info.title }}</h3>
    <h4>Voto: {{ info.vote_average }}</h4>
    <h4>Lingua: {{ info.original_language }}</h4>
    <lang-flag :iso="info.original_language" />
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "filmCard",
  components: {
    LangFlag,
  },
  // è arrivato della Main
  props: {
    info: Object,
  },
};
</script>

<style lang="scss">
.card {
  color: rgb(15, 13, 13);
  border: 1px solid gray;
}
</style>