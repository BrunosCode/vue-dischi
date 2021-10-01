<template>
  <div id="app">
    <Header/>
    <Collection/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Collection from './components/Collection.vue';

export default {
  name: 'App',
  components: {
    Header,
    Collection
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Roboto', sans-serif;
}
</style>
