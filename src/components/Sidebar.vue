<script setup lang="ts">
const props = defineProps({
  coordHistory: Array<string>,
})
</script>

<template>
  <div id="sidebar">
    <h2 id="sidebar-title">Selection History</h2>
    <div id="sidebar-history">
      <p v-if="!coordHistory || coordHistory?.length == 0" class="fadein-top-down">Looks like you haven't selected any
        squares yet. Click a square on the board to add it to your history.</p>
      <p v-else v-for="(coord, index) in coordHistory" :key="coordHistory.length - index"
        class="fadein-top-down fit-content">
        <span>{{ `${coordHistory.length - index}. ` }}</span>
        {{ `${coord}` }}
      </p>
    </div>
  </div>
</template>

<style scoped>
#sidebar {
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  flex-shrink: 0;
  border: solid 1px #aaa;
  border-radius: 0.375rem;
  background: white;
}

#sidebar-title {
  color: rgb(60, 60, 60);
  font-weight: 700;
  padding: 1rem;
  background: rgb(220, 220, 220);
}

#sidebar-history {
  display: flex;
  overflow-y: auto;
  flex-direction: column;
  width: 100%;
  padding: 1rem 0 1rem 0;
  gap: 0.5rem;
}

#sidebar-history>p {
  padding: 0 1rem 0 1rem;
}

#sidebar-history>p>span {
  color: rgb(100, 100, 100);
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
  animation: 0.4s slidein 1;
}

.fit-content {
  width: fit-content;
}
</style>
