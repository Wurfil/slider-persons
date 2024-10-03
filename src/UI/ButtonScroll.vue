<template>
  <button class="circle-button">
    <svg-icon class="icon" type="mdi" path="public/icons/arrow.svg" :size="48"></svg-icon>
  </button>
</template>

<script setup lang="ts">
import SvgIcon from '@jamescoyle/vue-icon'

defineProps<{
  direction: string
}>()
</script>

<style lang="scss" scoped>


.circle-button {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background-color: white;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: background-color 0.3s ease, box-shadow 0.3s ease;

  &:hover {
    background-color: #f0f0f0;
    box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
  }

  .arrow-icon {
    font-size: 20px;
    color: black;
    transition: transform 0.3s ease;
  }
}
</style>
