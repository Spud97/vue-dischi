<template>
  <div class="card d-flex flex-column text-center p-3 mt-3">
    <img :src="info.poster" alt="" />
    <h4>{{ info.title.toUpperCase() }}</h4>
    <span>{{ info.author }}</span>
    <span>{{ info.year }}</span>
  </div>
</template>

<script>
export default {
  name: "TheCard",
  props: {
    info: Object,
  },
};
</script>

<style lang="scss" scoped>
img {
  height: 170px;
}
h4 {
  color: white;
  font-size: 1.2rem;
  padding-top: 1.1rem;
  padding-bottom: 0.7rem;
}
span {
  font-size: 0.8rem;
  color: #737678;
}
.card {
  border-radius: 0;
  background-color: #2e3a46;
  height: 350px;
}
</style>
