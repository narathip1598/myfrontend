<!-- src/components/ItemList.vue -->
<template>
  <div>
    <h1>Items List</h1>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }} - {{ item.description }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      items: [],
    };
  },
  created() {
    this.fetchItems();
  },
  methods: {
    async fetchItems() {
      try {
        const response = await axios.get('http://localhost:8000/api/items/');
        this.items = response.data;
      } catch (error) {
        console.error('Error fetching items:', error);
      }
    },
  },
};
</script>