<script setup lang="ts">
import { useProductStore } from '../stores/product-store'

const store = useProductStore()

const previousPage = () => {
  if (store.page > 1) {
    store.page--
  }
}

const nextPage = () => {
  if (store.page < store.totalPages) {
    store.page++
  }
}

const goToPage = (page: number) => {
  store.page = page
}
</script>

<template>
  <div class="pagination">
    <button class="pagination-btn" @click="previousPage" :disabled="store.page === 1">
      Anterior
    </button>

    <div class="pagination-numbers">
      <button
        v-for="page in store.totalPages"
        :key="page"
        class="pagination-number"
        :class="{ active: store.page === page }"
        @click="goToPage(page)"
      >
        {{ page }}
      </button>
    </div>

    <button class="pagination-btn" @click="nextPage" :disabled="store.page === store.totalPages">
      Siguiente
    </button>
  </div>
</template>

<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
  margin-top: 2rem;
}

.pagination-btn {
  padding: 0.5rem 1rem;
  border: 2px solid #4f46e5;
  background: white;
  color: #4f46e5;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.3s;
}

.pagination-btn:hover:not(:disabled) {
  background: #4f46e5;
  color: white;
}

.pagination-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.pagination-numbers {
  display: flex;
  gap: 0.25rem;
}

.pagination-number {
  width: 40px;
  height: 40px;
  border: 2px solid #e0e0e0;
  background: white;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.3s;
}

.pagination-number:hover {
  border-color: #4f46e5;
}

.pagination-number.active {
  background: #4f46e5;
  color: white;
  border-color: #4f46e5;
}
</style>
