<template>
  <div class="home">
    <section>
      Basic Pagination with default <code>pageParamter</code> value:
    <vue-pagination
      :total-pages="12"
    />
    </section>
    <section>
      Pagination with custom <code>pageParameter</code> value:
      <vue-pagination
        :total-pages="13"
        page-parameter="tweetPages"
      />
    </section>
    <section style="font-family: monospace">
      <strong>Console</strong><br>
      <textarea
        ref="console"
        style="font-family: inerhit; min-width: 320px; max-width: 640px; width: 100%"
      />
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import VuePagination from '@/components/VuePagination.vue';

export default {
  name: 'Home',
  components: {
    VuePagination,
  },
  watch: {
    $route(to) {
      this.$refs.console.value += `\nRoute Change detected: page: ${to.query.page} / tweetPages: ${to.query.tweetPages}`;
    },
  },
};
</script>
