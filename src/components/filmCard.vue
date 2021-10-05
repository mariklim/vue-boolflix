<template>
<div class="card">
    <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->
    <p>Titolo: {{info.title}}</p>
    <p>Titolo originale: {{info.original_title}}</p>
     <p>Voto: {{info.vote_average}}</p>
     <p>Lingua: {{info.original_language}}</p>
</div>
  
</template>

<script>
export default {
    name: "filmCard",
    // è arrivato della Main
    props: {
        info: Object
  },

}
</script>

<style lang="scss">
.card{
    color: rgb(15, 13, 13);
    background-color: rgb(136, 219, 161);
    border: 1px solid gray;
}

</style>