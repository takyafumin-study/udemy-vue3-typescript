<script setup lang="ts">
import { Tweet } from "@/types/tweet";

defineProps<{
  tweet: Tweet;
}>();

const emits = defineEmits<{
  (e: "delete", id: string): void;
}>();

/**
 * onDelete
 *
 * @param id
 */
const onDelete = (id: string) => {
  emits("delete", id);
};
</script>

<template>
  <div class="tweet">
    <span>{{ tweet.description }} </span>
    <button @click="() => onDelete(tweet.id)">Delete</button>
  </div>
</template>

<style scoped></style>
