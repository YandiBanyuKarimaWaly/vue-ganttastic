<template>
  <div
    class="g-grid-cursor-time"
    :style="{
      // TODO: Fix the offset
      left: `${$props.leftOffset-10}px`
    }"
  >
    <div
      class="g-grid-cursor-time-marker"
      :style="{
        border: `1px dashed ${colors.markerCursorTime}`
      }"
    />
    <span class="g-grid-cursor-time-text" :style="{ color: colors.markerCursorTime }">
      <slot name="cursor-time-label">
        {{ cursorTimeLabel }}
      </slot>
    </span>
  </div>
</template>

<script setup lang="ts">
import provideConfig from "../provider/provideConfig.js"
const { colors, cursorTimeLabel } = provideConfig()
defineProps(['leftOffset'])
</script>

<style>
.g-grid-cursor-time {
  position: absolute;
  height: 100%;
  display: flex;
  z-index: 5;
  pointer-events: none;
}

.g-grid-cursor-time-marker {
  width: 0px;
  height: calc(100% - 2px);
  display: flex;
}

.g-grid-cursor-time-text {
  font-size: x-small;
}
</style>
