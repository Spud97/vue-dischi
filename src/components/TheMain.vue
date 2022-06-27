<template>
  <div>
    <div class="container py-5">
      <div class="row row-cols-5">
        <div class="col" v-for="(disc, i) in discList" :key="disc.title + i">
          <TheCard :info="disc"></TheCard>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import TheCard from "./TheCard.vue";
import { state } from "../store";
export default {
  name: "TheMain",
  components: { TheCard },
  props: {
    searchGenre: String,
  },
  data() {
    return {
      apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
      discList: [],
    };
  },
  computed: {
    filteredAlbums() {
      if (!state.genereSelezionato) {
        return this.discList;
      }
      return this.discList.filter((disc) => {
        return disc.genre === state.genereSelezionato;
      });
    },
    genereSelezionato() {
      return state.genereSelezionato;
    },
  },
  methods: {
    fetchData() {
      state.loading = true;
      axios
        .get(this.apiURL)
        .then((resp) => {
          this.discList = resp.data.response;
          state.listaGeneri = this.listaGeneri();
          setTimeout(() => {
            state.loading = false;
          }, 1000);
        })
        .catch(() => {
          alert(
            "A causa di un problema, l'operazione non è andata a buon fine."
          );
        });
    },
    listaGeneri() {
      const lista = [];
      this.discList.forEach((disc) => {
        if (!lista.includes(disc.genre)) {
          lista.push(disc.genre);
        }
      });
      return lista;
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>

<style lang="scss" scoped></style>
