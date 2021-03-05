<template>
  <div class="movies">
    <!-- https://www.w3schools.com/howto/tryit.asp?filename=tryhow_css_hero_image -->
    <div
      class="container-fluid p-0 header-container hero-image"
      :style="{
        backgroundImage: `linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url(${baseImageUrl +
          results[0].backdrop_path})`,
      }"
      v-if="dataReady"
    >
      <div class="hero-text">
        <h1 style="font-size:50px">{{ results[0].title }}</h1>
        <p>{{ results[0].release_date.substring(0, 4) }}</p>
        <div class="d-inline mr-5">
          <div class="stars-outer">
            <div class="stars-inner"> {{ results[0].vote_average }}</div>
          </div>
        </div>
        <button
          class="d-inline ml-5 btn btn-transparent border-warning text-warning"
        >
          Got To Movie
        </button>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-12 col-md-11 col-lg-8 mx-auto">
          <div class="card custom-category p-3 p-md-1">
            <div class="row">
              <div class="col-12 col-md-4">
                <h3 class="text-center text-md-left m-0 p-3">
                  Categories & Filters
                </h3>
              </div>
              <div class="col-6 col-sm-2 p-0 mx-auto">
                <p class="m-0 list" @click="getResult('popular')">
                  <small>Popular</small>
                </p>
                <p class="m-0 list" @click="getResult('top_rated')">
                  <small>Top Rated</small>
                </p>
                <p class="m-0 list" @click="getResult('upcoming')">
                  <small>Upcoming</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('28')">
                  <small>Action</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('12')">
                  <small>Adventure</small>
                </p>
              </div>
              <div class="col-6 col-sm-2 p-0 mx-auto">
                <p class="m-0 list" @click="getResultGenres('16')">
                  <small>Animation</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('35')">
                  <small>Comedy</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('80')">
                  <small>Crime</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('99')">
                  <small>Documentary</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('18')">
                  <small>Drama</small>
                </p>
              </div>
              <div class="col-12 col-sm-2 p-0 mx-auto">
                <p class="m-0 list" @click="getResultGenres('10751')">
                  <small>Family</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('14')">
                  <small>Fantasy</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('36')">
                  <small>History</small>
                </p>
                <p class="m-0 list" @click="getResultGenres('10749')">
                  <small>Romance</small>
                </p>
                <p class="m-0 list" @click="getResult('popular')">
                  <small>All Movies</small>
                </p>
              </div>
            </div>
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
            v-bind:src="baseImageUrl + result.poster_path"
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
      baseImageUrl: "https://image.tmdb.org/t/p/original",
      starsTotal: 5,
    };
  },
  methods: {
    getRatings(rating) {
      // https://codepen.io/bradtraversy/pen/GQLRZv?editors=1010
      const starPercentage = ((rating/2) / this.starsTotal) * 100;

      // Round to nearest 10
      const starPercentageRounded = `${Math.round(starPercentage / 10) * 10}%`;

      // Set width of stars-inner to percentage
      document.querySelector(
        `.stars-inner`
      ).style.width = starPercentageRounded;
    },
    getResult(filter) {
      const baseUrl = "https://api.themoviedb.org/3/movie/";
      const selectedFilter = filter;
      const api = "f9c3ae91ea7132ed424564f73bb859e0";
      axios
        .get(baseUrl + selectedFilter + "?api_key=" + api)
        .then((response) => {
          this.results = response.data.results;
          const rating = this.results[0].vote_average
          this.getRatings(rating)
        });
    },
    getResultGenres(filter) {
      const baseUrl = "https://api.themoviedb.org/3/";
      const selectedFilter = filter;
      const api = "f9c3ae91ea7132ed424564f73bb859e0";
      axios
        .get(
          baseUrl +
            "discover/movie?api_key=" +
            api +
            "&with_genres=" +
            selectedFilter
        )
        .then((response) => {
          this.results = response.data.results;
          const rating = this.results[0].vote_average
          this.getRatings(rating)
        });
    },
  },
  async mounted() {
    await this.getResult("popular");
    this.dataReady = true;
  },
};
</script>
