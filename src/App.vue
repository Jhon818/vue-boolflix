<template>
  <div id="app">
   
    <Header @startSearch="startSearch" />
    <Cards :moviesList="movieList" />

  </div>
</template>

<script>
import Cards from './components/Cards.vue';
import Header from './components/Header.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Cards,
  },
    data() {
        return {  
          movieList: [],
          APIurl: "https://api.themoviedb.org/3/search/movie?api_key=72fd9500b954a9cf78a65ac500e01314&query=",
          inputText: 'test'
         }
    },
    created() {
        this.getMovies()
    },
    methods: {
        getMovies() {
            axios
                .get(this.APIurl + this.inputText)
                    .then( res => {
                        this.moviesList = res.data.results;
                        console.log(this.moviesList)
                    })
        },
        startSearch(text) {
          console.log(text)
          this.inputText = text;

            for (var i in this.moviesList) {
                if (this.moviesList[i].original_title) {
                  // console.log(this.moviesList[i]); 
                }

                 if (text == this.moviesList.original_title) {
                
                return this.moviesList[i].original_title
              }

                if (text == this.moviesList.title) {
                
                return this.moviesList[i].title
              }

              if (text == this.moviesList.vote_average) {
                
                return this.moviesList[i].vote_average
              }
              console.log(this.moviesList[i].vote_average)
              }
            

             
            
        }
    }

  
}
</script>

<style lang="scss">
 @import "/style/general.scss";

</style>
