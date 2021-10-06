<template>
  <header>
    <div class="logo">
      <img
        src="https://image.tmdb.org/t/p/original/wwemzKWzjKYJFfCeiB57q3r4Bcm.svg"
        alt="logo"
      />
    </div>

    <div class="nav">
      <div class="searchbar">
        <input type="text" v-model="inputText" placeholder="cerca film e serial TV" />
        <!-- al click mando dati della input al padre App -->
        <button type="submit" @click.prevent="$emit('search', inputText)">
          Search
        </button>
      </div>
    </div>
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

<style lang="scss">
header {
  display: flex;
  height: 4.375rem;
  overflow: hidden;
  position: fixed;
  top: 0;
  width: 100%;
}

.logo {
  width: 6.25rem;
  img {
    width: 100%;
  }
}

.nav{
  text-align: right;
  width: 80%;
    .searchbar{
      display: inline-block;

        & input{
          width: 15.625rem;
          height: 2.1875rem;
          margin: 0 .625rem;
          background-color: black;
          color: white;
          border: 1px solid white;
          border-radius: 0;
        }
    }
}
</style>