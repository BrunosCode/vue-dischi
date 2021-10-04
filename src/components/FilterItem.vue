<template>
  <select v-model="filterValue" @change="emitFilter"
  class="c-filter" name="filter" id="filter" placeholder>
    <option value="" selected>All</option>
    <option value="Rock">Rock</option>
    <option value="Metal">Metal</option>
    <option value="Jazz">Jazz</option>
    <option value="Pop">Pop</option>
  </select>
</template>

<script>
export default {
  name: 'FilterItem',
  data() {
    return {
      filterValue: "",
    }
  },
  methods: {
    // Method passing the filter to the parent
    emitFilter: function() {
      this.$emit("filter-value", this.filterValue);
    }
  }  
}
</script>

<style scoped lang="scss">
@import "../assets/style/common.scss";

.c-filter {
  padding: .5rem 1rem;
  background-color: $primary-bg;
  color: $primary-text;
  border: none;
}

</style>
