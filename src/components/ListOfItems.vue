<script setup>
import { ref } from 'vue'
// import Items from './components/Items.vue'

const list = ref([])

fetch('http://localhost:3000/lists/')
  .then((response) => response.json())
  .then((data) => (list.value = data))
  
  // returned in list 
  [
  ({
    id: 1,
    title: 'Sample shopping list',
    items: [{ id: 1, 'item-name': 'toilet paper', purchased: false }],
    updatedAt: '2018-01-01T00:00:00.000Z'
  },
  {
    title: 'Costco',
    items: [
      { itemName: 'avocados', purchased: false },
      { itemName: 'bread', purchased: false }
    ],
    updatedAt: '2023-12-17T19:59:18.829Z',
    id: 2
  },
  {
    title: 'Wholefoods',
    items: [
      { itemName: 'tiramasu', purchased: false },
      { itemName: 'yogurt', purchased: false }
    ],
    updatedAt: '2023-12-17T19:59:18.829Z',
    id: 3
  })
]
</script>

<!-- Add :key="item.id" to v-for -->
<template>
  <div>
    <ul>
      <li v-for="item in list">
        {{ item.title }} - {{ item.items.length }}
        <div>
          <li v-for="item in list">
            {{ item }}
          </li>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
