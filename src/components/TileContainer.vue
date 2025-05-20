<template>
  <div class="tile-container">
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
// 无需额外逻辑
</script>

<style scoped>
.tile-container {
  display: flex;
  flex-wrap: wrap;
  padding: 16px;
  background-color: #000;
  min-height: 100vh;
}
</style>