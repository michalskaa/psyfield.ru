<script setup lang="ts">
import { useRepo } from '../../composables/repo'

const repo = useRepo()
</script>

<template lang="pug">
.flex.items-center.border-b-0.ml-3.space-x-4.mx-4
  a.icon-button(v-if="repo" :href="repo.link" target="_blank")
    carbon-logo-github
  nav-dark-mode
</template>

<style scoped >
.icon-button {
  @apply rounded-lg p-2 bg-gray-200
  bg-opacity-50 hover:bg-opacity-60
  focus:outline-none
  dark:(bg-gray-700 bg-opacity-60 hover:bg-opacity-70);
}
</style>
