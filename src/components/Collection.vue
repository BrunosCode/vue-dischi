<template>
  <div class="c-collection">
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
  data: function() {
    return {
      music: []
    }
  },
  mounted: function() {
    axios
      .get('https://flynn.boolean.careers/exercises/api/array/music')
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

</style>
