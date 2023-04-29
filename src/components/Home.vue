<template>
  <div>
    <div>
      <label for="textinput"> add item </label>
      <input id="textinput" v-model="keyword" type="text" />

      <button class="add" @click="addItem()">add</button>
    </div>
    <ul>
      <li v-for="(item, i) in items" :key="i">
        {{ item.name }}
        <button class="icon" @click="deleteItem(i)">-</button>
      </li>
    </ul>
  </div>
</template>
<script>
import { ref } from "vue";

export default {
  setup() {
    const keyword = ref("");
    let items = [];
    function addItem() {
      if (keyword.value) {
        items.push({ name: keyword.value });
        console.log("asas", items);
        keyword.value = "";
      }
    }

    function deleteItem(index) {
      items.splice(index)
      items = items
      console.log(items);
    }

    return {
      deleteItem,
      keyword,
      items,
      addItem,
    };
  },
};
</script>
<style>
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
