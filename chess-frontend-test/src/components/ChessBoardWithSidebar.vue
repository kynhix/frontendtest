<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'
import Sidebar from './Sidebar.vue'

const boardContainerRef = ref<HTMLDivElement>(null);
const boardRef = ref<HTMLDivElement>(null);
const dimension = ref('0px');
const lastSelectedCoord = ref('');
const selectedCoordHistory = ref<Array<string>>([]);
const selectedCoordColumn = ref(-1);
const selectedCoordRow = ref(-1);

const onResize = (event: ResizeObserverEntry[]) => {
  const { width, height } = event[0].contentRect;
  const minDimension = Math.trunc(Math.min(width, height) / 8) * 8;
  dimension.value = `${minDimension}px`;
}
const observer = new ResizeObserver(onResize);

const onClickBoard = ((event: MouseEvent) => {
  const { x, y, width } = boardRef.value.getBoundingClientRect();
  const realX = event.x - x;
  const realY = event.y - y;
  const column = Math.trunc(realX / Math.max(width, 1) * 8);
  const columnChar = String.fromCharCode('a'.charCodeAt(0) + column);
  const row = 8 - Math.trunc(realY / Math.max(width, 1) * 8);
  const coordString = columnChar.concat(row.toString());
  if (lastSelectedCoord.value == coordString) {
    return;
  }
  selectedCoordHistory.value.unshift(coordString);
  lastSelectedCoord.value = coordString;
  selectedCoordColumn.value = column;
  selectedCoordRow.value = 8 - (row);
})

onMounted(() => {
  observer.observe(boardContainerRef.value);
})

onUnmounted(() => {
  observer.unobserve(boardContainerRef.value);
})
</script>

<template>
  <div id="board-sidebar-container">
    <div id="board-container" ref="boardContainerRef">
      <div id="board" ref="boardRef" @click="onClickBoard">
        <div id="board-background">
          <svg version="1.1" width="100%" viewBox="0 0 128 128" xmlns="http://www.w3.org/2000/svg">
            <!-- Background pattern -->
            <defs>
              <pattern id="Pattern" x="0" y="0" width="32" height="32" patternUnits="userSpaceOnUse">
                <rect x="0" y="0" width="16" height="16" class="light-square"></rect>
                <rect x="16" y="0" width="16" height="16" class="dark-square"></rect>
                <rect x="0" y="16" width="16" height="16" class="dark-square"></rect>
                <rect x="16" y="16" width="16" height="16" class="light-square"></rect>
              </pattern>
            </defs>
            <rect fill="url(#Pattern)" width="128" height="128"></rect>
            <!-- Rank and file identifiers  -->
            <text x="12.25" y="126" font-size="3.5" class="light-square">a</text>
            <text x="28.25" y="126" font-size="3.5" class="dark-square">b</text>
            <text x="44.25" y="126" font-size="3.5" class="light-square">c</text>
            <text x="60.25" y="126" font-size="3.5" class="dark-square">d</text>
            <text x="76.25" y="126" font-size="3.5" class="light-square">e</text>
            <text x="92.25" y="126" font-size="3.5" class="dark-square">f</text>
            <text x="108.25" y="126" font-size="3.5" class="light-square">g</text>
            <text x="124.25" y="126" font-size="3.5" class="dark-square">h</text>
            <text x="1.5" y="116.25" font-size="3.5" class="light-square">1</text>
            <text x="1.5" y="100.25" font-size="3.5" class="dark-square">2</text>
            <text x="1.5" y="84.25" font-size="3.5" class="light-square">3</text>
            <text x="1.5" y="68.25" font-size="3.5" class="dark-square">4</text>
            <text x="1.5" y="52.25" font-size="3.5" class="light-square">5</text>
            <text x="1.5" y="36.25" font-size="3.5" class="dark-square">6</text>
            <text x="1.5" y="20.25" font-size="3.5" class="light-square">7</text>
            <text x="1.5" y="4.25" font-size="3.5" class="dark-square">8</text>
          </svg>
        </div>
        <div id="selected-square"></div>
      </div>
    </div>
    <Sidebar id="sidebar" :coordHistory="selectedCoordHistory" />
  </div>
</template>

<style scoped>
#board-sidebar-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  width: 100%;
  flex-grow: 1;
}

@media (min-width: 1024px) {
  #board-sidebar-container {
    flex-direction: row;
    align-items: start;
    justify-content: center;
    height: 100%;
  }
}

#board-container {
  display: flex;
  justify-content: center;
  overflow: hidden;
  flex-grow: 1;
  aspect-ratio: 1/1;
  width: 100%;
  max-width: calc(100vh - 2rem);
}

@media (min-width: 1024px) {
  #board-container {
    justify-content: end;
  }
}

#board-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

#board {
  position: relative;
  width: v-bind(dimension);
  overflow: hidden;
}

#selected-square {
  z-index: 1;
  position: absolute;
  transform: translate(calc(100% * v-bind(selectedCoordColumn)), calc(100% * v-bind(selectedCoordRow)));
  aspect-ratio: 1/1;
  width: 12.5%;
  background: rgba(255, 0, 0, 0.5);
}
</style>
