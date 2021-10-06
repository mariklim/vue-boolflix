<template>
  <header>
    <div class="logo">
      <img src="https://image.tmdb.org/t/p/original/wwemzKWzjKYJFfCeiB57q3r4Bcm.svg" alt="logo  ">
    </div>

    <div class="nav">
    <input type="text" v-model="inputText" />
    <!-- al click mando dati della input al padre App -->
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
    };
  },
};
</script>

<style lang="scss">
@import "../assets/style/variables.scss";
@import "../assets/style/common.scss";
header{
  display: flex;
  height: 4.375rem;
  overflow: hidden; 
  position: fixed; 
  top: 0; 
  width: 100%;
}
.logo .nav{
  border: 1px solid white;
}
.logo{
  width: 6.25rem;
    img{
      width: 100%;
    }
}

</style>