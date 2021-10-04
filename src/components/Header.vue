<template>
  <div class="c-header">
    <img class="c-header__logo" src="../assets/images/spotify-logo.png" alt="Logo Spotify">
    <label>
      <span class="c-header__label">Filter Genres</span>
      <FilterItem @filter-value="emitFilter"/>  
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
  methods: {
    // Method passing the filter to the parent
    emitFilter: function(string) {
      this.$emit("filter-value", string);
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
  justify-content: space-between;
  align-items: center;

  &__logo {
    height: 3rem;
  }

  &__label {
    color: $primary-text;
    margin-right: .75rem;
  }
}
</style>