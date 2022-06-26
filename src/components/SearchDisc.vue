<template>
  <form class="d-flex">
    <div class="input-group">
      <input
        type="text"
        class="form-control"
        placeholder="Genere musicale"
        v-model="searchText"
      />
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
export default {
  props: {
    genere: String,
  },
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    makeSearch() {
      this.$emit("search", this.searchText);
    },
    makeReset() {
      this.$emit("reset");
    },
  },
};
</script>

<style scoped lang="scss"></style>
