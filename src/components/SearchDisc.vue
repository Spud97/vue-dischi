<template>
  <form class="d-flex">
    <div class="input-group">
      <select type="text" class="form-select" v-model="genre">
        <option value="">Scegli un genere</option>
        <option v-for="(genere, i) in listaGeneriFromState" :key="i" :value="genere">
          {{ genere }}
        </option>
      </select>
      <button class="btn btn-outline-primary" type="button" @click="makeSearch">
        Cerca
      </button>
      <button class="btn btn-outline-secondary" type="reset" @click="makeReset">
        Reset
      </button>
    </div>
  </form>
</template>

<script>
import { state } from "../store";
export default {
  props: {
    listaGeneri: Array,
  },
  data() {
    return {
      genre: "",
    };
  },
  computed: {
    listaGeneriFromState() {
      return state.listaGeneri;
    },
  },
  methods: {
    makeSearch() {
      state.genereSelezionato = this.genre;
    },
     makeReset(){
      state.genereSelezionato = "";
    }
  },
};
</script>

<style scoped lang="scss"></style>
