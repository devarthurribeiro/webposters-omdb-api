<template>
  <div class="film">
    <img
      :src="
        film.Poster == 'N/A'
          ? 'http://www.valmorgan.com.au/wp-content/uploads/2016/06/default-movie-1-3.jpg'
          : film.Poster
      "
    />
    <div class="description">
      <h1>{{ film.Title }}</h1>
      <p>{{ film.Year }}</p>
      <p>{{ film.Type }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["film"],
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-size: 18px;
  font-weight: normal;
}
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
img {
  border-radius: 10px;
  width: 180px;
  height: auto;
}
.film {
  text-align: center;
  margin: 8px;
}
.description {
  margin-left: 8px;
}
</style>
