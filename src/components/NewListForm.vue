<script setup>
  import { ref } from "vue"; 
  const newStore = ref("")
  const newItem = ref("")
  const emit = defineEmits(["listCreated"]);

  const resetListForm = () => {
    newStore.value = "";
    newItem.value = "";
};
// const itemsArr = []
// // potatos, milk 
// let itemsObject = {

// }
// 

// newItem.value.split(" ")
const addToList = () => {
  fetch("http://localhost:3000/lists/", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({ title: newStore.value.trim(), items: [ ], updatedAt: new Date() }),
  })
    .then((response) => response.json())
    .then((data) => {
      emit("listCreated", data);
      resetListForm();
    });
};
</script>

<template>
  <div>
    <form @submit.prevent="addToList">
    <fieldset>
      <legend>Add some groceries!</legend>
      <label>
        Store
        <input v-model="newStore" id="text" name="store" />
      </label>
      <label>
        Items
        <input v-model="newItem" type="text" id="item" />
      </label>
      <input type="submit" value="Add" />
    </fieldset>
  </form>
  </div>
</template>

<style scoped>
</style>