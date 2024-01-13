<script setup lang="ts">
import { ref, reactive } from "vue";

const itemName2 = ref<string>("Bike");

const item1 = reactive({
  name: "Desk",
  price: 40000,
});

const price2 = 20000;

const url1 = "https://www.amazon.co.jp/dp/B07CMTX1VB";
const url2 = "https://www.amazon.co.jp/dp/B000ZKRE9U";

const buy = (itemName: string) => {
  alert("Aer you sure to buy " + itemName + "?");
};

/**
 * Clear input
 */
const clear = () => {
  item1.name = "";
  item1.price = 0;
};
</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input type="text" v-model="item1.name" />
    <input type="text" v-model="item1.price" />
    <button v-on:click="clear">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ item1.price }}円</label>
      <a v-bind:href="url1">Amazon</a>
      <button v-on:click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }}円</label>
      <a v-bind:href="url2">Amazon</a>
      <button v-on:click="buy(itemName2)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>
