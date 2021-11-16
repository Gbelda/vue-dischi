<template>
  <div class="pt-5">
    <label for="genre">Choose a Genre:</label>
    <select
      class="form-select"
      name="genre"
      id="genre"
      v-model="genreType"
      @change="$emit('filter-genre', genreType)"
    >
      <option selected value="">All</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      genreType: "",
    };
  },
};
</script>

<style>
</style>