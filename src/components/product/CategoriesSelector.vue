<script setup lang="ts">
import { useProductStore } from '../../stores/product-store'
import ArrowDown from '../common/icons/ArrowDown.vue'
import { capitalize } from '../../lib/utils'

const store = useProductStore()
</script>

<template>
  <div class="category-container">
    <select v-model="store.selectedCategory" @change="store.page = 1" class="category-select">
      <option value="all">Todas las categorías</option>
      <option v-for="category in store.categories" :key="category" :value="category">
        {{ capitalize(category) }}
      </option>
    </select>
    <ArrowDown />
  </div>
</template>

<style scoped>
.category-select {
  appearance: none;
  border-radius: 0.25rem;
  border: 1px solid #b8b6b66d;
  background-color: #f1f1f14b;
  padding: 0.5rem 1rem;
  color: #333;
  font-size: 14px;
  cursor: pointer;
  outline: none;
  padding-right: 2rem;
  width: 100%;
}

.category-container {
  position: relative;
  width: 100%;
}

@media (min-width: 768px) {
  .category-select {
    width: auto;
  }

  .category-container {
    width: auto;
  }
}
</style>
