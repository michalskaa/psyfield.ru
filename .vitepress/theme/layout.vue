<template lang="pug">
.theme(:class="pageClasses")
  nav-bar(v-if="showNavbar" @toggle="toggleSidebar")
  div(class="pt-$header-height min-h-screen" :class="{ 'grid-layout': !enableHome }")
    sidebar(:open="openSideBar")
    .sidebar-mask(@click="toggleSidebar(false)")
    home(v-if="enableHome")
    page(v-else)
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue'
import {
  useRoute,
  useData,
} from 'vitepress'
import { isSideBarEmpty, getSideBarConfig } from './support/sideBar'

// generic state
const route = useRoute()
const { site, theme } = useData()

// home
const enableHome = computed(() => !!route?.data?.frontmatter?.home)

// navbar
const showNavbar = computed(() => {
  if (!route.data) return true
  const { frontmatter } = route.data
  if (frontmatter.navbar === false || theme.value.navbar === false)
    return false

  return (
    site.value.title
    || theme.value.logo
    || theme.value.repo
    || theme.value.nav
  )
})

// sidebar
const openSideBar = ref(false)

const showSidebar = computed(() => {
  if (!route.data) return true
  const { frontmatter } = route.data

  if (frontmatter.home || frontmatter.sidebar === false)
    return false

  return !isSideBarEmpty(
    getSideBarConfig(theme.value.sidebar, route.data.relativePath),
  )
})

const toggleSidebar = (to?: boolean) => {
  openSideBar.value = typeof to === 'boolean' ? to : !openSideBar.value
}

const hideSidebar = toggleSidebar.bind(null, false)
// close the sidebar when navigating to a different location
watch(route, hideSidebar)
// TODO: route only changes when the pathname changes
// listening to hashchange does nothing because it's prevented in router

// page classes
const pageClasses = computed(() => {
  return [
    {
      'no-navbar': !showNavbar.value,
      'sidebar-open': openSideBar.value,
      'no-sidebar': !showSidebar.value,
    },
  ]
})
</script>

<style >
@screen lg {
  .grid-layout {
    display: grid;
    grid-template-columns: 16rem minmax(100px, 1fr);
    grid-template-rows: 1fr;
    gap: 0px 16px;
  }
}

/* @screen lg {
  .grid-layout {
    grid-template-columns: min-content minmax(100px, 2fr) 16rem;
  }
} */

#ads-container {
  margin: 0 auto;
}

@media (min-width: 420px) {
  #ads-container {
    position: relative;
    right: 0;
    float: right;
    margin: -8px -8px 24px 24px;
    width: 146px;
  }
}

@media (max-width: 420px) {
  #ads-container {
    /* Avoid layout shift */
    height: 105px;
    margin: 1.75rem 0;
  }
}

@media (min-width: 1400px) {
  #ads-container {
    position: fixed;
    right: 8px;
    bottom: 8px;
  }
}
</style>
