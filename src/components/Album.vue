<template>
  <div class="row pt-5 justify-content-center main_content">
    <div
      class="col-12 col-sm-6 col-md-4 col-lg-3 col-xxl-2 pt-5"
      v-for="album in albums"
      :key="album.title"
    >
      <div class="album text-center m-auto">
        <img :src="album.poster" alt="" />
        <h3 class="title">{{ album.title.toUpperCase() }}</h3>
        <h5 class="meta_data">
          {{ album.author }}
          <span class="year">{{ album.year }}</span>
        </h5>
      </div>
    </div>
  </div>
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
.main_content {
  padding-bottom: 6rem;
  .album {
    min-height: 400px;
    background-color: $secondary_bg;
    min-width: 196px;
    max-width: 196px;
    img {
      height: 200px;
      padding: 1rem;
      width: 200px;
    }
    .title {
      padding-bottom: 2rem;
      color: white;
    }
    .meta_data {
      color: $secondary_text;
      .year {
        display: block;
      }
    }
  }
}
</style>