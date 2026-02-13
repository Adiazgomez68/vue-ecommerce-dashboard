<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<style scoped>
.container {
  padding: 1rem;
  font-family: Arial, Helvetica, sans-serif;
  max-width: 1200px;
  margin: 0 auto;
}

@media (min-width: 1024px) {
  .container {
    padding: 0.5rem;
  }
}
</style>
