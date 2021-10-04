<template>
  <div class="c-header">
    <img class="c-header__logo" src="../assets/images/spotify-logo.png" alt="Logo Spotify">
    <label class="c-header__input">
      <span class="c-header__label">Filter Genres</span>
      <FilterItem @filter-value="emitGenresFilter" :options-list="filterLists.collectionGenres"/>  
    </label>
    <label class="c-header__input">
      <span class="c-header__label">Filter Authors</span>
      <FilterItem @filter-value="emitAuthorsFilter" :options-list="filterLists.collectionAuthors"/>  
    </label>
    <label class="c-header__input">
      <span class="c-header__label">Filter Years</span>
      <FilterItem @filter-value="emitYearsFilter" :options-list="filterLists.collectionYears"/>  
    </label>
  </div>
</template>

<script>
import FilterItem from "./FilterItem.vue";

export default {
  name: 'Header',
  components: {
    FilterItem
  },
  props: {
    filterLists: Object
  },
  methods: {
    // Method passing the filter to the parent
    emitGenresFilter: function(string) {
      this.$emit("genres-filter", string);
    },
    // Method passing the filter to the parent
    emitAuthorsFilter: function(string) {
      this.$emit("authors-filter", string);
    },
    // Method passing the filter to the parent
    emitYearsFilter: function(string) {
      this.$emit("years-filter", string);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../assets/style/common.scss";

.c-header {
  padding: 1rem;
  background-color: $secondary-bg;
  display: flex;
  justify-content: flex-end;
  align-items: center;

  &__logo {
    height: 3rem;
    margin-right: auto;
  }

  &__input {
    margin-right: 2rem;
  }

  &__label {
    color: $primary-text;
    margin-right: .75rem;
  }
}
</style>