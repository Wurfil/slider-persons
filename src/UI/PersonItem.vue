<template>
  <div class="profile">
    <img :src="image" alt="profile" />
    <p>{{ name }}</p>
  </div>
</template>
<script setup lang="ts">
defineProps<{
  image: string
  name: string
}>()
</script>

<style scoped lang="scss">
.profile {
  text-align: center;
  width: 160px;
  img {
    width: 144px;
    height: 144px;
    border-radius: 50%;
  }
  p {
    color: black;
    font-weight: $font-semi-bold;
    word-spacing: 9999px;
    margin-top: 10px;
    font-size: $base-font-size;
  }
}
</style>
