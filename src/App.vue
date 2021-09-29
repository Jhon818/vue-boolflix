<template>
  <div id="app" class="bg-secondary">
    <Header @startSearch="startSearch" />
    <Cards :filteredList="filteredMoviesList" :filteredTvList="filteredTvList" />
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
      apiSearchingSeries: "https://api.themoviedb.org/3/search/tv?api_key=72fd9500b954a9cf78a65ac500e01314&language=en-US&page=1&query=",
      APIkey:"72fd9500b954a9cf78a65ac500e01314&query=",
      TvText: 'tv',
      inputText: 'test',
    };
  },
  created() {
    this.getMovies();
    this.getSeries();
  },
  computed: {
    filteredMoviesList() {
      if (this.inputText === "") {
        console.log(this.moviesList)
        return this.moviesList;
      }
      let filteredList = this.moviesList.filter((item) => {
        return item.title.toLowerCase().includes(this.inputText.toLowerCase());
      });
      console.log(filteredList)
      return filteredList;
    },

    filteredTvList() {
      if (this.inputText !== "") {
        return this.seriesList
      }
      let filteredTvList = this.seriesList.filter((item) => {
        return item.name.toLowerCase().includes(this.inputText.toLowerCase());
         });
      return filteredTvList
    }
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
        .get(this.apiSearchingSeries + this.inputText)
        .then((res) => {
          this.seriesList = res.data.results;
        })
        .catch((err) => {
          console.log("Error ", err);
        });
    },
    startSearch(text) {
      this.inputText = text;
      this.getSeries(),
      this.getMovies()
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
