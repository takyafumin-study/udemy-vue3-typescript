<script setup lang="ts">
import { ref, inject } from "vue";
import { userNameKey, updateUserNameKey } from "@/key";

const props = defineProps({
  show: Boolean,
});

const emits = defineEmits<{
  (e: "close"): void;
}>();

const username = inject<string>(userNameKey, "");
const currentUsername = ref<string>(username);

const updateUserName = inject<(value: string) => void>(
  updateUserNameKey,
  () => { },
);

const onClose = () => {
  updateUserName(currentUsername.value);
  emits("close");
};
</script>

<template>
  <div v-if="props.show" class="modal-mask">
    <div class="modal-container">
      <div class="modal-header">
        <slot name="header">Fill Username</slot>
      </div>

      <div class="modal-body">
        <slot name="body">
          <input type="text" v-model="currentUsername" />
        </slot>
      </div>

      <div class="modal-footer">
        <slot name="footer">
          <button class="modal-default-button" @click="onClose">OK</button>
        </slot>
      </div>
    </div>
  </div>
</template>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 300px;
  margin: auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-body {
  margin: 20px 0;
}

.modal-default-button {
  float: right;
}

input {
  width: 100%;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
