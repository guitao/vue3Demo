<template>
  <h1>{{ msg }}</h1>
  <h2>Filter LearnVue Articles</h2>
  <input type="text" placeholder="Filter Search" v-model="query" />
  <button @click="reset">clear</button>

  <search-results :query='query'/>
</template>

<script>
import { ref } from "vue";
import SearchResults from './SearchResults.vue'

export default {
  name: "HelloWorld",
  components: {
    SearchResults
  },
  props: {
    msg: String,
  },
  setup() {
    const query = ref("");

    const reset = (e) => {
      query.value = ''
    }

    return {
      query,
      reset
    };
  },
};
</script>
