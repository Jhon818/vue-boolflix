<template>
  <div id="app" class="bg-secondary">
    <Header @startSearch="startSearch" />
    <Cards :filteredList="filteredMoviesList" />
  </div>
</template>

<script>
import Cards from "./components/Cards.vue";
import Header from "./components/Header.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Cards,
  },
  data() {
    return {
      moviesList: [],
      seriesList: [],
      APIurl:
        "https://api.themoviedb.org/3/search/movie?api_key=72fd9500b954a9cf78a65ac500e01314&query=",
      inputText: "Test",
    };
  },
  created() {
    this.getMovies();
    this.getSeries();
  },
  computed: {
    filteredMoviesList() {
      if (this.inputText === "") {
        return this.moviesList;
      }
      let filteredList = this.moviesList.filter((item) => {
        return item.title.toLowerCase().includes(this.inputText.toLowerCase());
      });
      return filteredList;
    },

    filteredSeriesList() {
      if (this.inputText === "") {
        return this.moviesList;
      }
      let filteredSeries = this.moviesList.filter((item) => {
        return item.title.toLowerCase().includes(this.inputText.toLowerCase());
      });
      return filteredSeries;
    },
  },
  methods: {
    getMovies() {
      axios
        .get(this.APIurl + this.inputText)
        .then((res) => {
          this.moviesList = res.data.results;
        })
        .catch((err) => {
          console.log("Error ", err);
        });
    },
    getSeries() {
      axios
        .get(this.APIurl + "tv")
        .then((res) => {
          this.seriesList = res.data.results;
        })
        .catch((err) => {
          console.log("Error ", err);
        });
    },
    startSearch(text) {
      this.inputText = text;
    },
  },
};
</script>

<style lang="scss">
@import "/style/general.scss";
#app {
  font-weight: 700;
}
</style>
