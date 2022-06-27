<template>
  <div class="bg-header">
    <div class="container d-flex justify-content-between">
      <div>
        <i class="fa-brands fa-spotify spotify-icon my-2"></i>
      </div>
      <div class="d-flex align-items-center">
        <SearchDisc
          :lista-generi="listaGeneri"
          @searchGenre="$emit('searchGenre', $event)"
        >
        </SearchDisc>
      </div>
    </div>
  </div>
</template>

<script>
import SearchDisc from "./SearchDisc.vue";
export default {
  name: "TheHeader",
  components: { SearchDisc },
  props: {
    listaGeneri: Array,
  },

  methods: {
    onSearchChange() {
      return this.discList.filter((disc) => {
        return disc.name
          .toLowerCase()
          .includes(this.searchText.trim(" ").toLowerCase());
      });
    },
    onSearchReset() {
      this.searchText = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.bg-header {
  background-color: #2e3a46;
}

.spotify-icon {
  color: #1dd65f;
  height: 3rem;
}
</style>
