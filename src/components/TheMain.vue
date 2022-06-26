<template>
  <div>
    <div class="container py-5">
      <div class="row row-cols-5">
        <div class="col" v-for="disc in discList" :key="disc.title">
        <TheCard :info="disc"></TheCard>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import TheCard from './TheCard.vue';
export default {
    name: "TheMain",
    components: { TheCard },
    data() {
    return {
      apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
      discList: [],
    };
  },
  methods: {
    fetchDiscList() {
      axios.get(this.apiURL)
      .then((resp) => {
        this.discList = resp.data.response
      })
    },
  },
  mounted() {
    this.fetchDiscList()
  }
};
</script>

<style lang="scss" scoped></style>
