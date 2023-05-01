<template>
  <div>
    <div>
      <label for="textinput"> add item </label>
      <input id="textinput" v-model="keyword" type="text" />

      <button class="add" @click="addItem()">add</button>
    </div>
    <ul>
      <li v-for="(item, i) in items" :key="i">
        <div class="flex">
          <div >{{ item.name }}</div>
          <div><button class="icon" @click="deleteItem(i)">-</button></div>
        </div>
      </li>
    </ul>
  </div>
</template>
<script setup>
import { ref } from "vue";

const keyword = ref("");
const items = ref([]);

const addItem = () => {
  if (keyword.value) {
    items.value.push({ name: keyword.value });
    keyword.value = "";
  }
};

const deleteItem = (i) => {
  items.value = items.value.filter((t) => {
    t != i;
  });
};
</script>
<style>
.flex {
  align-items: center;
  flex-wrap: wrap;
  display: flex;
  justify-content: space-between;
}
.add {
  margin: 6px;
}
.icon-button {
  align-items: end;
}
input {
  height: 30px;
}
ul {
  list-style-type: none;
}
li {
  padding: 10px;
  border: 1px;
  border-bottom: 1px;
  border-style: solid;
  border-width: 0 0 1px 0;
  text-align: left;
  width: 300px;
}
</style>
