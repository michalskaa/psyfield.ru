<template lang="pug">
header.nav-bar
  nav-toggle-sidebar(@toggle="$emit('toggle')")
  nav-bar-title
  div(class="hidden lg:flex px-3 ml-4 lg:ml-10")
    nav-links
  .flex-grow
  nav-dark-mode
</template>

<script setup>
defineEmits(['toggle']);
</script>

<style scoped lang="postcss">
.nav-bar {
  @apply fixed top-0 inset-x-0 z-$z-index-navbar flex space-between align-center select-none border-b-1px border-$c-divider py-0.7rem px-4 h-$header-height bg-$c-bg md: px-5 lg:px-6;
}

.nav-bar.root {
  @apply border-transparent bg-$c-bg-semi;
}
</style>
