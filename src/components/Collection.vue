<template>
  <div class="c-collection l-container">
    <Album v-for="(album, i) in music" :key="i" :album-data="album"/>
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
    apiUrl: String
  },
  data: function() {
    return {
      music: []
    }
  },
  mounted: function() {
    axios
      .get(this.apiUrl)
      .then((response) => {
        this.music.push(...response.data.response);
      })
      .catch((error) => {
        console.log(error);
      });
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
