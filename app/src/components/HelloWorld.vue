<script setup lang="ts">
import { ref } from "vue";

type Tweet = {
  id: string;
  description: string;
};

const tweets = ref<Array<Tweet>>([
  { id: "1", description: "Hello!" },
  { id: "2", description: "Example" },
]);
const tweet = ref<Tweet>({ id: "", description: "" });

/**
 * submit
 */
const onSubmit = () => {
  tweets.value = [
    ...tweets.value,
    {
      id: Math.random().toString(),
      description: tweet.value.description,
    },
  ];

  tweet.value = { id: "", description: "" };
};

const onDelete = (id: string) => {
  tweets.value = tweets.value.filter((tweet) => tweet.id !== id);
};

/** 検索テキスト */
const search = ref<string>("");
</script>

<template>
  <h1>Twitter</h1>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="tweet.description" />
    <button type="submit">Tweet</button>
  </form>
  <input type="text" v-model="search" />

  <ul>
    <li v-for="(tweet, key) in tweets" :key="key">
      <div v-if="tweet.description.includes(search)">
        <span>{{ tweet.description }} </span>
        <button @click="() => onDelete(tweet.id)">Delete</button>
      </div>
    </li>
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
