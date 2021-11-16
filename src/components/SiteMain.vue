<template>
  <main>
    <div class="container">
      <div class="mb-1">
        <label for="genre" class="form-label">Select</label>
        <select class="form-select" name="genre" id="genre">
          <option value="0">All</option>
          <option value="1">Rock</option>
          <option value="2">Pop</option>
          <option value="3">Jazz</option>
          <option value="4">Metal</option>
        </select>
      </div>
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