<template>
  <div class="bg-header">
    <div class="container d-flex justify-content-between">
      <div>
        <i class="fa-brands fa-spotify spotify-icon my-2"></i>
      </div>
      <div class="d-flex align-items-center">
        <SearchDisc>
          @search="onSearchChange" @reset="onSearchReset" :genere="genere"
        </SearchDisc>
      </div>
    </div>
  </div>
</template>

<script>
import discList from "./TheMain.vue";
import SearchDisc from "./SearchDisc.vue";
export default {
  name: "TheHeader",
  components: { SearchDisc },
  props: {
    genere: String,
  },
  data() {
    return {
      discList,
      searchText: ""
    }
  },
  computed: {
    getGenresList() {
      const list = [];
      this.discList.forEach((disc) => {
        if (!list.includes(disc.genre)) {
          list.push(disc.genre);
        }
      });
      return list;
    },
  },
  methods: {
    onSearchChange() {
      return this.discList.filter((disc) => {
        return disc.genre
          .toLowerCase()
          .includes(this.searchText.trim(" ").toLowerCase());
      });
    },
    onSearchReset() {
      this.searchText = ""
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
