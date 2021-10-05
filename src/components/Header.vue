<template>
<header>
    <input type="text" v-model="inputText">
    <button type="submit"  @click.prevent="$emit('search', inputText)">Search</button>

</header>
</template>

<script>
export default {
    name: "Header"

}
</script>

<style>

</style>