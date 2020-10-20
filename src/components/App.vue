<template>
  <div class="app">
    <Header :title="'Vue with Composition API Sample'" />
    <Search :search="state.search" @search="handleSearch" />
    <div class="movies">
      <Movie v-for="movie in state.movies" :movie="movie" :key="movie.imdbID" />
    </div>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Search from "./Search.vue";
import Movie from "./Movie.vue";
import { useMovieApi } from "../hooks/movie-api";

export default {
  name: "app",
  components: { Header, Search, Movie },
  setup() {
    const state = useMovieApi();

    return {
      state,
      handleSearch(searchTerm) {
        state.loading = true;
        state.search = searchTerm;
      },
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  font-size: 10px;
}

.app {
  text-align: center;
}

.header {
  background-color: darkslategray;
  height: 70px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
  padding: 20px;
  cursor: pointer;
}

.header > div {
  font-size: 2.5rem;
}

.spinner {
  height: 80px;
  margin: auto;
}

.movies {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: center;
}

.movie__title {
  font-size: 2rem;
  height: 50px;
  flex: 0 0 20%;
}

.movie {
  padding: 5px 25px 10px 25px;

  flex: 0 0 20%;
}

.movie > p {
  font-size: 1.2rem;
}

.errorMessage {
  margin: auto;
  font-weight: bold;
  color: rgb(161, 15, 15);
}

.search {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  margin: 20px 0px;
}

input[type="submit"] {
  padding: 5px;
  background-color: transparent;
  color: black;
  border: 2px solid black;
  width: 80px;
  margin-left: 5px;
  cursor: pointer;
  font-size: 1.2rem;
}

input[type="submit"]:hover {
  background-color: darkslategray;
  color: antiquewhite;
}

.search > input[type="text"] {
  width: 40%;
  min-width: 170px;
  font-size: 2rem;
  padding: 5px 10px;
  border: 2px solid black;
}

@media screen and (min-width: 694px) and (max-width: 915px) {
  .movie {
    max-width: 33%;
  }
}

@media screen and (min-width: 652px) and (max-width: 693px) {
  .movie {
    max-width: 50%;
  }
}

@media screen and (max-width: 651px) {
  .movie {
    max-width: 100%;
    margin: auto;
  }
}
</style>
