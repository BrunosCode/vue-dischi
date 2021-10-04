<template>
  <div class="c-collection l-container">
    <Album v-for="(album, i) in collection" :key="i" :album-data="album"/>
  </div>
</template>

<script>
import Album from "./Album.vue"

export default {
  name: 'Collection',
  components: {
    Album
  },
  props: {
    collection: Array
  },
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
