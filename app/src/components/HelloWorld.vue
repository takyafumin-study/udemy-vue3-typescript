<script setup lang="ts">
import { ref } from "vue";

const tweets = ref<Array<string>>(["Tweet1", "Tweet2", "Tweet3"]);
</script>

<template>
  <h1>Twitter</h1>
  <ul>
    <li v-for="(tweet, key) in tweets" :key="key">{{ tweet }}</li>
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}

li {
  margin-top: 1rem;
}
</style>
