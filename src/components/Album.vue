<template>
  <div>
    <SelectGenre @filter-genre="getGenre" />
    <SelectArtist :artists="filterAlbum" @filter-artist="getArtist" />
    <div class="row pt-5 justify-content-center main_content" v-if="!loading">
      <div
        class="col-12 col-sm-6 col-md-4 col-lg-3 col-xxl-2 pt-5"
        v-for="album in filterArtist"
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
    <div class="loading" v-else>
      <h1>LOADING....</h1>
    </div>
    <div>
      <h2 v-if="filterArtist == 0 && loading == false">
        There is no Album available...
      </h2>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SelectGenre from "./SelectGenre.vue";
import SelectArtist from "./SelectArtist.vue";
export default {
  components: {
    SelectGenre,
    SelectArtist,
  },
  data() {
    return {
      albums: [],
      error: "",
      loading: true,
      genre: "",
      artist: "",
    };
  },
  methods: {
    callAPI() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.albums = response.data.response;
          this.loading = false;
        })
        .catch((error) => {
          alert(error);
        });
    },
    getGenre(text) {
      this.genre = text;
    },
    getArtist(text) {
      this.artist = text;
    },
  },
  computed: {
    filterAlbum() {
      return this.albums.filter((album) => {
        return album.genre.indexOf(this.genre) > -1;
      });
    },
    filterArtist() {
      return this.filterAlbum.filter((artist) => {
        return artist.author.indexOf(this.artist) > -1;
      });
    },
  },
  mounted() {
    setTimeout(() => {
      this.callAPI();
    }, 1000);
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
.loading {
  padding-top: 5rem;
  color: white;
  text-align: center;
}
h2 {
  color: red;
  text-align: center;
}
</style>