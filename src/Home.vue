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

.movie-images {
  width: 100%;
}

.custom-category {
  z-index: 999;
  transform:translate(0px, -20px);
}

.list {
  height: 18px;
  cursor: pointer;
}

.list:hover,
.list:focus,
.list:active {
  text-decoration: underline;
}

.hero-image {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}

.hero-text {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}

.hero-text button {
  border: none;
  outline: 0;
  display: inline-block;
  padding: 10px 25px;
  color: black;
  background-color: #ddd;
  text-align: center;
  cursor: pointer;
}

.hero-text button:hover {
  background-color: #555;
  color: white;
}
</style>
