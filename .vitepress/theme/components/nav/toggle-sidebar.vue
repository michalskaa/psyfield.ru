<template>
  <div class="sidebar-button -ml-2 text-xl" @click="emit('toggle')">
    <ri-menu-4-fill />
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits(['toggle'])
</script>

<style>
.sidebar-button {
  @apply cursor-pointer h-full inline-flex px-2 items-center lg:hidden;
}
</style>
