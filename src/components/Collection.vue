<template>
  <div class="c-collection l-container">
    <Album v-for="(album, i) in filteredCollection" :key="i" :album-data="album"/>
  </div>
</template>

<script>
import Album from "./Album.vue"

const axios = require("axios");

export default {
  name: 'Collection',
  components: {
    Album
  },
  props: {
    apiUrl: String,
    collectionFilter: String
  },
  data: function() {
    return {
      collection: []
    }
  },
  created: function() {
    axios
      .get(this.apiUrl)
      .then((response) => {
        this.collection.push(...response.data.response);
      })
      .catch((error) => {
        console.log(error);
      });
  },
  computed: {
    filteredCollection: function() {
      return this.collection.filter(album => album.genre.includes(this.collectionFilter));
    },
  }
  
}
</script>

<style scoped lang="scss">
.c-collection {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: auto auto;
  column-gap: 1rem;
  row-gap: 2rem;
}
</style>
