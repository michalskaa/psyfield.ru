<script setup lang="ts">
import { computed } from 'vue'
import { useRoute } from 'vitepress'

const route = useRoute()
const headers = computed(() => {
  return route.data.headers || []
})
</script>

<template lang="pug">
aside(class="hidden lg:block h-full")
  .headers-sidebar(v-if="headers.length")
    div(class="sidebar-link-item head !pl-0 !mb-1")
      | Sections
    ul(class="sidebar-links space-y-1.5")
      li.sidebar-link(v-for="item of headers" :key="item.title")
        // '!ml-0 !ml-4 !ml-8 !ml-16'
        a.sidebar-link-item(:href="`#${item.slug}`" :class="`!ml-${(item.level - 2) * 4} ${item.level > 2 ? 'text-sm opacity-65' : ''}`")
          | {{ item.title }}
</template>

<style scoped >
.headers-sidebar {
  height: calc(100vh - var(--header-height));
  @apply sticky top-$header-height py-7 px-6 overflow-y-auto;
}
</style>
