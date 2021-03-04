<template>
  <div class="movies">
    <div class="container-fluid p-0 header-container" v-if="dataReady">
        <img class="landing-image"
          v-bind:src="'https://image.tmdb.org/t/p/original' + results[0].poster_path"/>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-12 col-md-6 offset-md-3">
          <div class="card custom-category">
            <p @click="getResult('popular')">Popular</p>
            <p @click="getResult('top_rated')">Top Rated</p>
          </div>
        </div>
      </div>
      <div class="row">
        <div
          class="col-11 col-sm-6 col-md-4 col-lg-3 p-2 mx-auto"
          v-for="result in results"
          :key="result.id"
        >
          <img
            class="movie-images"
            v-bind:src="
              'https://image.tmdb.org/t/p/original' + result.poster_path
            "
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      dataReady: false,
      results: "",
    };
  },
  methods: {
    getResult(category) {
      const baseUrl = "https://api.themoviedb.org/3/movie/";
      const selectedCategory = category;
      const api = "f9c3ae91ea7132ed424564f73bb859e0";
      axios
        .get(baseUrl + selectedCategory + "?api_key=" + api)
        .then((response) => {
          this.results = response.data.results;
        });
    },
  },
  async mounted() {
    await this.getResult('popular');
    this.dataReady = true;
  },
};
</script>
