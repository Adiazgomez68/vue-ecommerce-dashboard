<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <RouterView />
</template>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}

header {
  font-size: x-small;
}

input {
  border: 1px solid #b8b6b66d;
  padding: 10px;
  width: 100%;
  border-radius: 5px;
  background-color: #f1f1f14b;
  font-size: 14px;
}

select {
  border-radius: 4px;
  border: 1px solid #b8b6b6;
  padding: 8px;
}
</style>
