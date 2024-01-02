<script setup>
import ListOfShops from './components/ListOfShops.vue'
import NewListForm from './components/NewListForm.vue'
</script>

<template>
  <div>
    <h1>Vue Shopping List App</h1>
    <!-- your code here -->
  </div>
  <main>
    <NewListForm />
    <ListOfShops />
  </main>
</template>

<style scoped></style>

<!-- Testing in Insomnium
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
