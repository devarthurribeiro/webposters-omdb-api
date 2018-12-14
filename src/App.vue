<template>
  <div id="app">
    <h1>WEB Posters</h1>
    <div class="filter">
      <input
        v-model="filter"
        @keypress.enter="findFilms"
        placeholder="Pesquisar por..."
        type="text"
      />
      <br />
      <button @click="findFilms">Buscar</button>
    </div>
    <div v-for="film in films.Search" :key="film.imdbID" class="films">
      <HelloWorld :film="film" />
    </div>
    <footer>
      Created by
      <a href="https://github.com/devarthurribeiro" target="_blank"
        >Arthur Ribeiro</a
      >
      &
      <a href="https://github.com/PedroRicardo117" target="_blank">
        Pedro Fonsca
      </a>
    </footer>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
const URL_API = "https://www.omdbapi.com/?apikey=134fe33";
export default {
  name: "App",
  components: {
    HelloWorld
  },
  data() {
    return {
      filter: "",
      films: []
    };
  },
  methods: {
    findFilms() {
      fetch(`${URL_API}&s=${this.filter}`)
        .then(r => r.json())
        .then(list => {
          this.films = list;
          console.log(list);
        })
        .catch(err => {
          alert(err);
        });
    }
  }
};
</script>

<style>
body {
  margin: 0;
  background-color: #29292a;
}

footer {
  position: fixed;
  width: 100%;
  text-align: center;
  bottom: 8px;
}

button,
input {
  padding: 10px;
  margin: 8px;
  border-radius: 8px;
  border: none;
  font-size: 16px;
}

a {
  color: #fff;
}

input {
  background-color: rgba(0, 0, 0, 0.4);
  color: #fff;
}

input:focus {
  outline: none;
}

button {
  background-color: #e63e34;
  color: #fff;
  font-weight: 600;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 16px;
  color: #fff;
}

.filter {
  display: flex;
  justify-content: center;
}

.films {
  display: inline-flex;
}
</style>
