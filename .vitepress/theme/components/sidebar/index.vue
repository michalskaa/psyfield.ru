<template lang="pug">
aside(class="h-auto border-r-1px border-$c-divider")
  .sidebar(:class="{ open }")
    nav-links.nav
    sidebar-links

</template>

<script setup lang="ts">

defineProps({
  open: { type: Boolean, required: true },
})
</script>

<style scoped lang="postcss">
.sidebar {
  /* position: fixed;
  top: var(--header-height);
  bottom: 0;
  left: 0; */
  z-index: var(--z-index-sidebar);
  width: 16.4rem;
  background-color: var(--c-bg);
  overflow-y: auto;
  transform: translateX(-100%);
  transition: transform 0.25s ease;
  height: calc(100vh - var(--header-height));
  @apply fixed top-$header-height bottom-0 left-0 lg_sticky max-w-420;
}

@screen lg {
  .sidebar {
    transform: translateX(0);
  }
}

@media (min-width: 960px) {
  .sidebar {
    width: auto;
  }
}

.sidebar.open {
  transform: translateX(0);
}

.nav {
  display: block;
}

@screen lg {
  .nav {
    display: none;
  }
}
</style>
