<template>
  <div id="app">
    <Header @filter-value="saveFilter"/>
    <Collection :api-url="api" :collection-filter="filterValue"/>
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
  },
  data: function() {
    return {
      api: 'https://flynn.boolean.careers/exercises/api/array/music',
      filterValue: ""
    }
  },
  methods: {
    // Storing the filter
    saveFilter: function(string) {
      this.filterValue = string;
    }
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
