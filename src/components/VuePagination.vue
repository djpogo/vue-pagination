<template>
  <nav>
    <ul>
      <li>
        <router-link
          :to="paginateObject(currentPage - 1)"
        > « </router-link>
      <li>{{ currentPage }} / {{ totalPages }}</li>
      <li>
        <router-link
          :to="paginateObject(currentPage + 1)"
        > » </router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'vue-pagination',
  data() {
    return {
      currentPage: null,
    };
  },
  props: {
    totalPages: {
      type: Number,
      required: true,
    },
    pageParameter: {
      type: String,
      default: 'page',
    },
  },
  methods: {
    paginateObject(pageTo) {
      return {
        query: {
          ...this.$route.query,
          [this.pageParameter]: pageTo,
        },
      };
    },
  },
  mounted() {
    this.currentPage = parseInt(this.$route.query[this.pageParameter], 10) || 1;
  },
  watch: {
    $route(to) {
      this.currentPage = parseInt(to.query[this.pageParameter], 10) || 1;
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
}
li {
  display: inline-block;
}
</style>
