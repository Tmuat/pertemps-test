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
  height: 50vh;
  overflow: hidden;
}

.movie-images {
  width: 100%;
}

.custom-category {
  z-index: 999;
  -webkit-transform:translate(0px, -20px);
      -ms-transform:translate(0px, -20px);
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
  -webkit-transform: translate(-50%, -50%);
      -ms-transform: translate(-50%, -50%);
          transform: translate(-50%, -50%);
  color: white;
}

.hero-text button {
  text-align: center;
  cursor: pointer;
}

.hero-text button:hover {
  background-color: #555;
  color: white;
}

.stars-outer {
  position: relative;
  display: inline-block;
}

.stars-inner {
  position: absolute;
  top: 0;
  left: 0;
  white-space: nowrap;
  overflow: hidden;
  width: 0;
}

.stars-outer::before {
  content: "\f005 \f005 \f005 \f005 \f005";
  font-family: "Font Awesome 5 Free";
  font-weight: 900;
  color: #ccc;
}

.stars-inner::before {
  content: "\f005 \f005 \f005 \f005 \f005";
  font-family: "Font Awesome 5 Free";
  font-weight: 900;
  color: #f8ce0b;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background: rgb(0, 0, 0);
  background: rgba(0, 0, 0, 0.5); /* Black see-through */
  color: #f1f1f1;
  transition: .5s ease;
  opacity:0;
  color: white;
  font-size: 20px;
  text-align: center;
}

.card-overlay:hover .overlay,
.card-overlay:focus .overlay,
.card-overlay:active .overlay {
  opacity: 1;
}

.overlay .inner-overlay {
    position:relative;
    top:25%;
}
</style>
