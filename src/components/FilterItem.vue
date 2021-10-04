<template>
  <select v-model="filterValue" @change="emitFilter"
  class="c-filter" name="filter" id="filter" placeholder>
    <option value="" disabled selected>Select your option</option>
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
    emitFilter: function() {
      this.$emit("filter-value", this.filterValue);
    }
  },
  mounted() {
    console.log("filter" + this.filterValue);
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
