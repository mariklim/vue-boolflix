<template>
  <header>
    <input type="text" v-model="inputText" />

    <!-- al click mando dati della input al padre App -->
    <button type="submit" @click.prevent="$emit('search', inputText)">
      Search
    </button>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputText: "",
    };
  },
};
</script>

<style>
</style>