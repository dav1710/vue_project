<script setup>
import { ref, computed } from 'vue';

const products = ref([
  {title: 'Apple', price: 100.65},
  {title: 'Notebook', price: 700.50},
  {title: 'Phone', price: 1100.70},
  {title: 'Camera', price: 10000.5},
  {title: 'Samsung', price: 800.50},
  {title: 'Xiaomi', price: 90.50},
  {title: 'Shoes', price: 25.90},
  {title: 'T-Shirt', price: 99.99},
  {title: 'BMW', price: 59999.50}
]);

const query = ref('')
const queryProducts = computed(() => {
  let product = products.value;
  let search = query.value;

  if (search) {
    product = product.filter((p) => {
      return p.title.indexOf(search) !== -1 ||
      p.price.toString().indexOf(search) !== -1
    })
  }
  return product;
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
      {{ product.title }}
      <sup>{{ product.price.toLocaleString() }}💲</sup>
    </li>
  </ul>
</div>
</template>

