<script setup lang="ts">
const props = defineProps({
  clickedCoords: Array<string>,
})
</script>

<template>
  <div id="sidebar">
    <p v-if="!clickedCoords || clickedCoords?.length == 0" class="fadein-top-down">Click a coordinate on the boord.</p>
    <p v-else v-for="(coord, index) in clickedCoords" :key="index - clickedCoords.length" class="fadein-top-down">{{
      coord
      }}</p>
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

@keyframes slidein {
  0% {
    transform: translateY(-2rem);
  }

  100% {
    transform: translateY(0);
  }
}

.fadein-top-down {
  animation: 0.3s slidein 1;
}
</style>
