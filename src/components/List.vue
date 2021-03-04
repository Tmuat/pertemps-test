<template>
  <div class="movies">
    <div class="container-fluid p-0 header-container">
      <img class="landing-image"
        v-bind:src="'https://image.tmdb.org/t/p/original' + results[0].poster_path"
      />
    </div>
    <div class="container">
      <div class="row">
        <div
          class="col-12 col-md-3 p-2"
          v-for="result in results"
          :key="result.id"
        >
          <img
            v-bind:src="
              'https://image.tmdb.org/t/p/original' + result.poster_path
            "
            width="224"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "categories",
  data() {
    return {
      category: "popular",
      results: "",
    };
  },
  methods: {
    getResult() {
      const baseUrl = "https://api.themoviedb.org/3/movie/";
      const selectedCategory = this.category;
      const api = "f9c3ae91ea7132ed424564f73bb859e0";
      axios
        .get(baseUrl + selectedCategory + "?api_key=" + api)
        .then((response) => {
          this.results = response.data.results;
        });
    },
  },
  mounted() {
    this.getResult();
  },
};
</script>
