<template>
  <div id="app">
    <TheHeader :lista-generi="listaGeneri" @searchGenre="onSearchGenre"></TheHeader>
    <h1 v-if="loading" class="text-white">Loading...</h1>
    <TheMain @genresUpdated="onGenresUpdate" :search-genre="searchGenre"></TheMain>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheMain from "./components/TheMain.vue";
import { state } from "./store";

export default {
  name: "App",
  components: {
    TheHeader,
    TheMain,
  },
   data() {
    return {
      listaGeneri: [],
      searchGenre: "",
    };
  },
  computed: {
    loading() {
      return state.loading;
    },
  },
  methods: {
    onGenresUpdate(listaGeneri) {
      console.log("listaGeneri: ", listaGeneri);
      this.listaGeneri = listaGeneri;
    },
    onSearchGenre(genre) {
      this.searchGenre = genre;
    },
  },
  mounted() {},
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #1e2d3b;
}
</style>
