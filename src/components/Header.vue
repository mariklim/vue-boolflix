<template>
  <header>
      <div class="logo">
        <img
          src="https://image.tmdb.org/t/p/original/wwemzKWzjKYJFfCeiB57q3r4Bcm.svg"
          alt="logo"
        />
      </div>

      <div class="nav">
        <!-- <select name="genres" v-model="selected" @change="$emit('select', selected)">
          <option value="">Filtra per genere</option>
          <option v-for="(genre, id) in allGenres" :key="id" :value="genre.id" >
          {{ genre.name }}
      </option>
        </select> -->

        <div class="searchbar">
          <i class="fas fa-search"></i>
          <input type="text" v-model="inputText" placeholder="Filtra per titolo" >
          <!-- al click mando dati della input al padre App -->
        </div>
        <button type="submit" @click.prevent="$emit('search', inputText)">
          Search
        </button>
      </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputText: "",
      selected: "",
    };
  },
  props:{
    allGenres: Array,
  
  }
};
</script>

<style lang="scss">
@import "../assets/style/common";
header {
  display: flex;
  height: 4.375rem;
  overflow: hidden;
  position: fixed;
  top: 0;
  width: 100%;
}
.logo {
  width: 80px;
  img {
    width: 100%;
  }
}

.nav {
  text-align: right;
  width: 80%;
  button {
    height: 37px;
    background-color: transparent;
    color: white;
    border: 1px solid rgb(255, 255, 255);
    cursor: pointer;
    transition: background-color 1s;
  }

  button:hover {
    background-color: rgba(134, 134, 134, 0.801);
  }

  .searchbar {
    margin-left: .625rem;
    display: inline-block;
    border: 1px solid white;
    border-right: 0;
    color: rgba(255, 255, 255, 0.322);
    i {
      padding: 0 0.625rem;
    }
  
    & input {
      width: 15.625rem;
      height: 2.1875rem;
      background-color: black;
      color: white;
      border: 0;

      &:focus {
        outline: none;
      }
    }
  }
}
</style>