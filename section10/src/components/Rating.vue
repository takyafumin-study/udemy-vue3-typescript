<script setup lang="ts">
import { ref } from "vue";

const props = defineProps(["modelValue"]);
const emits = defineEmits(["update:modelValue"]);

const isActiveButton = ref<string>(props.modelValue);

const onClilck = (buttonType: string) => {
  isActiveButton.value = buttonType;
  emits("update:modelValue", isActiveButton.value);
};
</script>

<template>
  <ul>
    <li>
      <button :class="{ active: isActiveButton === 'bad' }" @click="onClilck('bad')" type="button">
        Bad
      </button>
    </li>
    <li>
      <button :class="{ active: isActiveButton === 'average' }" @click="onClilck('average')" type="button">
        Average
      </button>
    </li>
    <li>
      <button :class="{ active: isActiveButton === 'great' }" @click="onClilck('great')" type="button">
        Great
      </button>
    </li>
  </ul>
</template>

<style scoped>
.active {
  color: pink;
}

ul {
  list-style-type: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid gray;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>
