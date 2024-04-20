<template>
  <div class="board"></div>
</template>

<style scoped>
.board-container {
  background: red;
  flex-grow: 1;
}

.board {
  flex-shrink: 1;
  aspect-ratio: 1;
  background: green;
  width: min(100%, 100vh);
}
</style>
