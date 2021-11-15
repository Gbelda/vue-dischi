<template>
  <main>
    <div class="container">
      <Album />
    </div>
  </main>
</template>

<script>
import Album from "./Album.vue";
export default {
  components: {
    Album,
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";
main {
  min-height: calc(100vh - 80px);
  background-color: $main_bg;
}
</style>