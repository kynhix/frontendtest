<template>
  <div id="sidebar">
    <p>Click a coordinate on the boord.</p>
  </div>
</template>

<style scoped>
#sidebar {
  display: flex;
  overflow-x: hidden;
  overflow-y: auto;
  flex-direction: column;
  width: 100%;
  flex-shrink: 0;
  padding: 1rem;
  border: solid 1px #aaa;
  gap: 0.5rem;
  background: #ddd;
  height: 100%;
  border-radius: 0.375rem;
}

@media (min-width: 1024px) {
  #sidebar {
    width: var(--sidebar-width);
  }
}
</style>
