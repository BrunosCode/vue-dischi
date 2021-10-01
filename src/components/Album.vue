<template>
  <div class="c-album">
    <img :src="albumData.poster" :alt="albumData.title" class="c-album__img">
    <h3 class="c-album__title">{{albumData.title}}</h3>
    <p class="c-album__data">{{albumData.author}}</p>
    <p class="c-album__data">{{albumData.year}}</p>
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
@import "../assets/style/common.scss";

.c-album {
  display: flex;
  flex-direction: column;
  text-align: center;
  background-color: $secondary-bg;
  padding: 1rem;

  &__title {
    margin: 1rem 0 .5rem;
    color: $primary-text;
    text-transform: uppercase;
    font-weight: 400;
  }

  &__data {
    color: $secondary-text;
  }

  &__img {
    max-width: 100%;
  }
}
</style>
