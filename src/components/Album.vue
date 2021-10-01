<template>
  <div class="c-album">
    <img :src="albumData.poster" :alt="albumData.titole">
    <h3>{{albumData.titole}}</h3>
    <p>{{albumData.author}}</p>
    <p>{{albumData.year}}</p>
  </div>
</template>

<script>
export default {
  name: 'Collection',
  props: {
    albumData: Object
  },
  
}
</script>

<style scoped lang="scss">
.c-album {
  display: flex;
  flex-direction: col;
}
</style>
