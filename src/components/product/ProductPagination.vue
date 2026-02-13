<script setup lang="ts">
import { useProductStore } from '../../stores/product-store'
import ArrowLeft from '../common/icons/ArrowLeft.vue'
import ArrowRight from '../common/icons/ArrowRight.vue'

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
      <ArrowLeft />
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
      <ArrowRight />
    </button>
  </div>
</template>

<style scoped>
.pagination {
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.pagination-btn {
  padding: 0.5rem 0.5rem;
  background: white;
  color: #616162;
  border: 0;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pagination-btn:hover:not(:disabled) {
  background: #ececec;
  color: black;
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
  width: 30px;
  height: 30px;
  border: 1px solid #e0e0e0;
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
