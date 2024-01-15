<script setup lang="ts">
import { ref } from "vue";
import { Tweet } from "@/types/tweet";

const tweet = ref<Tweet>({
  id: "",
  description: "",
});

const emits = defineEmits<{
  (e: "submit", value: string): void;
}>();

/**
 * submit
 */
const onSubmit = (value: string) => {
  emits("submit", value);
  tweet.value = { id: "", description: "" };
};
</script>

<template>
  <div>
    <form class="tweet-form" @submit.prevent="() => onSubmit(tweet.description)">
      <textarea v-model="tweet.description"></textarea>
      <button type="submit">Tweet</button>
    </form>
  </div>
</template>

<style scoped></style>
