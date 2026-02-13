<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router'
import CloseIcon from './icons/CloseIcon.vue'
import ProductIcon from './icons/ProductIcon.vue'

defineProps<{
  isOpen: boolean
  onClose: () => void
}>()

const route = useRoute()
</script>

<template>
  <div v-if="isOpen" class="overlay" @click="onClose"></div>

  <aside :class="['sidebar', { 'sidebar-open': isOpen }]">
    <div class="sidebar-header mobile-only">
      <h2>Menú</h2>
      <button @click="onClose" class="close-btn" aria-label="Cerrar menú">
        <CloseIcon />
      </button>
    </div>

    <div class="sidebar-header desktop-only">
      <h2>Menú</h2>
    </div>

    <nav class="sidebar-nav">
      <ul>
        <li>
          <router-link
            to="/products"
            @click="onClose"
            :class="['menu-item', { active: route.path === '/products' }]"
          >
            <ProductIcon />
            <span>Productos</span>
          </router-link>
        </li>
      </ul>
    </nav>
  </aside>
</template>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 40;
}

.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  width: 256px;
  background-color: white;
  border-right: 1px solid #e5e7eb;
  z-index: 50;
  transform: translateX(-100%);
  transition: transform 0.3s ease-in-out;
  overflow-y: auto;
}

.sidebar-open {
  transform: translateX(0);
}

.sidebar-header {
  padding: 1.4rem;
  border-bottom: 1px solid #e5e7eb;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.sidebar-header h2 {
  font-size: 1rem;
  font-weight: 600;
  color: #1f2937;
  margin: 0;
}

.close-btn {
  padding: 0.5rem;
  border: none;
  background: none;
  border-radius: 8px;
  cursor: pointer;
  color: #4b5563;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.2s;
}

.close-btn:hover {
  background-color: #f3f4f6;
}

.sidebar-nav {
  padding: 1rem;
}

.sidebar-nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.sidebar-nav li {
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
}

.menu-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.5rem 0.8rem;
  border-radius: 8px;
  text-decoration: none;
  color: #374151;
  transition: background-color 0.2s;
}

.menu-item:hover {
  background-color: #f3f4f6;
}

.menu-item.active {
  background-color: #eef2ff;
  color: #4f46e5;
  font-weight: 500;
}

.mobile-only {
  display: flex;
}

.desktop-only {
  display: none;
}

@media (min-width: 1024px) {
  .overlay {
    display: none;
  }

  .sidebar {
    transform: translateX(0);
  }

  .mobile-only {
    display: none;
  }

  .desktop-only {
    display: flex;
  }
}
</style>
