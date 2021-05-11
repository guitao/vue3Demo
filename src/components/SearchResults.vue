<template>
  <div class="container">
    <h2>Showing {{ filteredTitles.length }} results for "{{ query }}"</h2>
    <hr />

    <ul>
      <li v-for="item in filteredTitles" :key="item.id">
        {{ item.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import { computed } from "vue";
import dataList from "../assets/posts.json";

export default {
  name: "SearchResults",
  props: {
    query: String,
  },
  setup(props) {
    const filteredTitles = computed(() => {
      return dataList.filter((s) =>
        s.title.toLowerCase().includes(props.query.toLowerCase())
      );
    });

    console.log("===filteredTitles===", filteredTitles);

    return {
      filteredTitles,
    };
  },
};
</script>

<style scoped>
ul {
    height: 50vh;
    overflow-y: scroll;
    display: flex;
    flex-direction: column;
    align-items: center;
    list-style: none;
    text-align: center;
}
li {
    width: 400px;
    border: 1px solid #dcdee2;
    border-radius: 6px;
    margin-bottom: 10px;
    padding: 15px 0;
}
</style>