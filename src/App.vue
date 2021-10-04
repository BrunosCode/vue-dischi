<template>
  <div id="app">
    <Header 
    @genres-filter="storeSelectedGenre" 
    @authors-filter="storeSelectedAuthor" 
    @years-filter="storeSelectedYear" 
    :filterLists="{collectionGenres, collectionAuthors, collectionYears}"/>

    <Collection :collection="filteredCollection"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Collection from './components/Collection.vue';

const axios = require("axios");

export default {
  name: 'App',
  components: {
    Header,
    Collection
  },
  data: function() {
    return {
      selectedGenre: "",
      selectedAuthor: "",
      selectedYear: "",
      collection: []
    }
  },
  created: function() {
    // Get collection from an API
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.collection.push(...response.data.response);
      })
      .catch((error) => {
        console.log(error);
      });
  },
  methods: {
    // Storing the filters
    storeSelectedGenre: function(string) {
      this.selectedGenre = string;
    },
    storeSelectedAuthor: function(string) {
      this.selectedAuthor = string;
    },
    storeSelectedYear: function(string) {
      this.selectedYear = string;
    },
  },
  computed: {
    // Generate a filtered collection when all the promises are fullfilled
    filteredCollection: function() {
      return this.collection.filter(album => album.genre.includes(this.selectedGenre))
                  .filter(album => album.author.includes(this.selectedAuthor))
                  .filter(album => album.year.includes(this.selectedYear));
    },
    // Generate an array with no duplicate items, to use as filter
    collectionGenres: function() {
      let genres = this.collection.map(album => album.genre);
      let genresSet = new Set(genres);
      return genresSet;
    },
    // Generate an array with no duplicate items, to use as filter
    collectionAuthors: function() {
      let authors= this.collection.map(album => album.author);
      let authorsSet = new Set(authors);
      return authorsSet;
    },
    // Generate an array with no duplicate items, to use as filter
    collectionYears: function() {
      let years= this.collection.map(album => album.year);
      let yearsSet = new Set(years);
      return yearsSet;
    },
  },
}
</script>

<style lang="scss">
@import "./assets/style/common.scss";

#app {
  font-family: 'Roboto', sans-serif;
  background-color: $primary-bg;
  min-height: 100vh;
}
</style>
