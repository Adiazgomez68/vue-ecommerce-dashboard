<script setup lang="ts">
import type { Product } from '../types/product'

defineProps<{
  product: Product
}>()
</script>

<template>
  <div class="product-detail">
    <div class="product-image">
      <img :src="product.image" :alt="product.title" />
    </div>
    <div class="product-info">
      <h2 class="product-title">{{ product.title }}</h2>
      <p class="product-description">{{ product.description }}</p>
      <p class="product-price">{{ product.price }}</p>
    </div>
  </div>
</template>

<style scoped>
.product-detail {
  display: flex;
  gap: 2rem;
}

.product-image {
  flex: 1;
}

.product-image img {
  width: 100%;
  height: auto;
}

.product-info {
  flex: 2;
}

.product-title {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.product-description {
  font-size: 1.2rem;
  margin-bottom: 1rem;
}

.product-price {
  font-size: 1.5rem;
  font-weight: bold;
}
</style>
