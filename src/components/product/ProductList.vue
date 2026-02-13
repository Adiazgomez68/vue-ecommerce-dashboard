<script setup lang="ts">
import type { Product } from '../../types/product'
import { useRouter } from 'vue-router'
import { capitalize, formatCurrency, formatRating } from '../../lib/utils'
import EyeIcon from '../common/icons/EyeIcon.vue'

const props = defineProps<{
  products: Product[]
}>()

const router = useRouter()

const gotToProductDetails = (id: number) => {
  router.push({ name: 'product-detail', params: { id } })
}
</script>

<template>
  <div class="product-list-container">
    <div class="table-wrapper">
      <table>
        <thead>
          <tr>
            <th>Ref</th>
            <th>Nombre</th>
            <th>Categoría</th>
            <th>Precio</th>
            <th>Rating</th>
            <th></th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="product in props.products" :key="product.id">
            <td>
              <img :src="product.image" :alt="product.title" class="product-image" />
            </td>

            <td>{{ product.title }}</td>
            <td>
              <span class="badge-category">
                {{ capitalize(product.category) }}
              </span>
            </td>
            <td>{{ formatCurrency(product.price) }}</td>
            <td>{{ formatRating(product.rating.rate) }}</td>

            <td>
              <button class="btn-detail" @click="gotToProductDetails(product.id)">
                <EyeIcon />
                <span>Ver detalle</span>
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.table-wrapper {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}

table {
  width: 100%;
  min-width: 600px;
  border-collapse: collapse;
  border-bottom: 1px solid #eeeded;
}

th {
  font-weight: 600;
  font-size: 13px;
  color: #797979;
  height: 25px;
  text-transform: uppercase;
  white-space: nowrap;
}

th,
td {
  padding: 0.5rem;
  padding-left: 14px;
  text-align: left;
  border-top: 1px solid #eeeded;
}

td {
  font-size: 14px;
}

.product-image {
  width: 50px;
  height: 50px;
  object-fit: contain;
}

.badge-category {
  display: inline-flex;
  align-items: center;
  border-radius: 0.25rem;
  background-color: #e5e7ebcf;
  padding: 0.25rem 0.5rem;
  font-size: 0.75rem;
  font-weight: 500;
  color: #1f2937;
  white-space: nowrap;
}

.btn-detail {
  color: rgb(142, 141, 141);
  display: flex;
  align-items: center;
  gap: 0.3rem;
  background-color: transparent;
  border: none;
  padding: 0.4rem 0.7rem;
  border-radius: 0.5rem;
  cursor: pointer;
  font-weight: 500;
  font-family: system-ui;
  transition: all 0.3s ease;
  font-size: 12.5px;
  white-space: nowrap;
}

.btn-detail:hover {
  color: #4f46e5;
  background-color: #eef2ff;
}
</style>
