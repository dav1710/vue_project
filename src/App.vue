<script setup>
import { ref, computed } from 'vue';

const products = ref([
    'Apple',
    'Notebook',
    'Phone',
    'Camera',
    'Samsung',
    'Xiaomi',
    'Shoes',
    'T-Shirt',
    'BMW'
]);

const query = ref('')
const queryProducts = computed(() => {
  return products.value.filter((product) => product.indexOf(query.value) !== -1);
})
</script>

<template>
<div>
  <input type="search"
         name="search"
         placeholder="Product Search"
         v-model="query"
  >
  <br><br><br>
  {{ query }}
  <br><br><br>

  <ul>
    <li v-for="product in queryProducts"
        :key="product">
      {{ product }}
    </li>
  </ul>
</div>
</template>

