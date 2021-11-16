<template>
  <div class="pt-5">
    <select
      class="form-select"
      name="genre"
      id="genre"
      v-model="genreType"
      @change="$emit('filter-genre', genreType)"
    >
      <option selected value="">All</option>
      <option value="1">Rock</option>
      <option value="2">Pop</option>
      <option value="3">Jazz</option>
      <option value="4">Metal</option>
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