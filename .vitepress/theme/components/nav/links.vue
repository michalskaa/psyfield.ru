<template>
  <nav v-if="show" class="nav-links">
    <template v-if="links">
      <div v-for="item in links" :key="item.text" class="item">
        <NavDropdownLink v-if="item.items" :item="item" />
        <NavLink v-else :item="item" />
      </div>
    </template>

    <div v-if="localeLinks" class="item">
      <NavDropdownLink :item="localeLinks" />
    </div>
  </nav>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useData } from 'vitepress'
import { useLocaleLinks } from '../../composables/nav.js'
import { useRepo } from '../../composables/repo'

const { site } = useData()
const localeLinks = useLocaleLinks()
const repo = useRepo()

const show = computed(() => links.value || repo.value)

const links = computed(() => site.value.themeConfig.nav)
</script>

<style lang="postcss" scoped>
.nav-links {
  padding: 0.75rem 0;
  border-bottom: 1px solid var(--c-divider);
}

@screen lg {
  .nav-links {
    display: flex;
    padding: 2px 0 0;
    align-items: center;
    border-bottom: 0;
  }

  .item + .item {
    padding-left: 24px;
  }
}
</style>
