<script setup lang="ts">
import ChessBoardWithSidebar from './components/ChessBoardWithSidebar.vue'
</script>

<template>
  <main id="layout">
    <ChessBoardWithSidebar />
  </main>
</template>

<style scoped>
#layout {
  padding: 0.5rem;
  overflow-x: hidden;
  overflow-y: auto;
  flex-flow: row;
  width: 100%;
  height: 100%;
}

@media (min-width: 1024px) {
  #layout {
    padding: 1rem;
  }
}
</style>
