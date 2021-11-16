<template>
  <div class="pt-4">
    <label for="artist">Choose an Artist:</label>
    <select
      class="form-select"
      name="artist"
      id="artist"
      v-model="artist"
      @change="$emit('filter-artist', artist)"
    >
      <option selected value="">All</option>
      <option
        v-for="artist in artists"
        :key="artist.author"
        :value="artist.author"
      >
        {{ artist.author }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    artists: Array,
  },
  data() {
    return {
      artist: "",
    };
  },
};
</script>

<style>
</style>