<template>
  <div id="app">
    <Header
    @search="searchFilm"
    />
    <Main
    :infoFilm = "inputText"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
		return {
			inputText: ""
		}
	},
  methods: {
		searchFilm(text) {
			this.inputText = text;
      console.log(this.inputText)
		}
	},
}
</script>

<style lang="scss">
</style>
