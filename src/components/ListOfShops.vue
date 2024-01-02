<script setup>
  import { ref } from "vue"
  import ListOfItems from './ListOfItems.vue'
  import NewListForm from './NewListForm.vue'
  
  const list = ref([])

  fetch("http://localhost:3000/lists/")
  .then((response) => response.json())
  .then((data) => (list.value = data))

  // [ { "id": 1, "title": "Sample shopping list", "items": [ { "id": 1, "item-name": "toilet paper", "purchased": false } ], "updatedAt": "2018-01-01T00:00:00.000Z" }, { "title": "Costco", "items": [ { "itemName": "avocados", "purchased": false }, { "itemName": "bread", "purchased": false } ], "updatedAt": "2023-12-17T19:59:18.829Z", "id": 2 }, { "title": "Wholefoods", "items": [ { "itemName": "tiramasu", "purchased": false }, { "itemName": "yogurt", "purchased": false } ], "updatedAt": "2023-12-17T19:59:18.829Z", "id": 3 } ]
</script>

<template>
  <div><NewListForm /></div>
  <div>
    <h1> shopping List Stores</h1>
  
    <!-- your code here -->
    <ul>
      <li v-for="item in list" :key="store.id">
        {{ item.title }} - {{ item.items.length }}
      </li>
    </ul>
  </div>
  <main>
    <ListOfItems />
  </main>
</template>

<style scoped>
</style>



<!-- Testing in Insomnium: POST
JSON.stringify({ title: "Costco", items: [{item-name: "avocados", purchased: false}, {item-name: "bread", purchased: false}] , updatedAt: new Date() })
})

actually sent 
{
  "title":"Costco",
  "items":
    [
      {
        "itemName":"avocados","purchased":false}
    ,
      {
        "itemName":"bread","purchased":false
      }
    ],

  "updatedAt":"2023-12-17T19:59:18.829Z"}

//problem with this request 
// doesn't give items their own id number 


-->
