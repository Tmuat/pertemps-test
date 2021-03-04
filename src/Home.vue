<template>
  <div id="home">
    <List />
  </div>
</template>

<script>
import List from "./components/List";
export default {
  name: "Home",
  components: {
    List,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.header-container {
  width: 100vw;
  height: 40vh;
  overflow: hidden;
}

.landing-image {
  width: 100%;
  background-position: center !important;
  background-repeat: no-repeat !important;
  background-size: cover !important;
  overflow: hidden;
}

.movie-images {
  width: 100%;
}

.custom-category {
  height: 100px;
  z-index: 999;
  transform:translate(0px, -20px);
}
</style>
