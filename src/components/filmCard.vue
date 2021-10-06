<template>
<div class="card">
    <!-- "info" è un singolo oggetto della array con i film, contiene tante info che ci servono -->
    <p>Titolo: {{info.title}}</p>
    <p>Titolo originale: {{info.original_title}}</p>
     <p>Voto: {{info.vote_average}}</p>
     <p>Lingua: {{info.original_language}}</p>
        <lang-flag :iso='info.original_language'/>
 
</div>
  
</template>

<script>
import LangFlag from 'vue-lang-code-flags'
export default {
    name: "filmCard",
    components: {
        LangFlag
    },
    // è arrivato della Main
    props: {
        info: Object
  },

}
</script>

<style lang="scss">
.card{
    color: rgb(15, 13, 13);
    border: 1px solid gray;
}

</style>