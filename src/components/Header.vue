<template>
  <div class="c-header">
    <img class="c-header__logo" src="../assets/images/spotify-logo.png" alt="Logo Spotify">
  </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.c-header {
  padding: .5rem;
  background-color: #2E3A46;

  &__logo {
    height: 3rem;
  }
}
</style>
