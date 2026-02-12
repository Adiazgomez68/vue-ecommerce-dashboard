<script setup lang="ts">
import WrapperContainer from '../components/WrapperContainer.vue'
import { useProductStore } from '../stores/product-store'
import { useRoute } from 'vue-router'
import { onMounted } from 'vue'
import ProductDetail from '../components/ProductDetail.vue'

const store = useProductStore()
const router = useRoute()

onMounted(() => {
  store.fetchProduct(Number(router.params.id))
})
</script>

<template>
  <WrapperContainer>
    <header class="header">
      <h1>Detalle del Producto</h1>
    </header>

    <div v-if="store.loadingProducts" class="loading">
      <span class="spinner"></span>
      <p>Cargando producto...</p>
    </div>

    <div v-else-if="store.productDetail" class="content">
      <ProductDetail :product="store.productDetail" />
    </div>

    <div v-else class="content">
      <p>No se encontró el producto.</p>
    </div>
  </WrapperContainer>
</template>

<style scoped>
.content {
  margin-top: 1.7rem;
}

.loading {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.spinner {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  border: 2px solid #ccc;
  border-top-color: #333;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
