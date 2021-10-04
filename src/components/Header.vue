<template>
  <div class="c-header">
    <img class="c-header__logo" src="../assets/images/spotify-logo.png" alt="Logo Spotify">
    <FilterItem @filter-value="emitFilter"/>  
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
}
</style>