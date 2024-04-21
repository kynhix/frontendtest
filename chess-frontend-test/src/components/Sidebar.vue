<script setup lang="ts">
const props = defineProps({
  clickedCoords: Array<string>,
})
</script>

<template>
  <div id="sidebar">
    <h1 id="sidebar-title">Selection History</h1>
    <hr>
    <div id="sidebar-history">
      <p v-if="!clickedCoords || clickedCoords?.length == 0" class="fadein-top-down">Click a coordinate on the boord.
      </p>
      <p v-else v-for="(coord, index) in clickedCoords" :key="index - clickedCoords.length"
        class="fadein-top-down fit-content">{{
          coord
        }}</p>
    </div>
  </div>
</template>

<style scoped>
hr {
  margin: 1rem 0 1rem 0;
}

#sidebar {
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  flex-shrink: 0;
  padding: 1rem;
  border: solid 1px #aaa;
  border-radius: 0.375rem;
  background: #ddd;
}

#sidebar-history {
  display: flex;
  overflow-y: auto;
  flex-direction: column;
  width: 100%;
  gap: 0.5rem;
}

@media (min-width: 1024px) {
  #sidebar {
    width: var(--sidebar-width);
  }
}

@keyframes slidein {
  0% {
    transform: translateX(calc(-100%));
  }

  100% {
    transform: translateX(0);
  }
}

.fadein-top-down {
  animation: 0.3s slidein 1;
}

.fit-content {
  width: fit-content;
}
</style>
