<template>
  <main>
    <div class="container">
      <div class="row">
        <div class="col-6"></div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      albums: [],
      error: "",
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.albums = response.data.response;
      })
      .catch((error) => {
        alert(error);
      });
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";
main {
  min-height: calc(100vh - 80px);
  max-height: calc(100vh - 80px);
  background-color: $main_bg;
}
</style>