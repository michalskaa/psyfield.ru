<template lang="pug">
a(
  class="hover:shadow",
  style="background-color: var(--c-bg);"
  :href="item.link", 
  :title="item.lastModified"
  )
  .info
    .flex.flex-1.items-center.self-stretch.flex-wrap
      .mr-2.text-2xl(v-if="item.data.emoji") {{ item.data.emoji }}
      h3.text-xl {{ item.title }}
      .flex.items-center.mx-2.text-sm.rounded-full.py-1.px-2(class="text-$c-brand bg-$c-bg-secondary",v-if="theme?.pages?.[item.data.list]") 
        .flex-1 {{ theme?.pages?.[item.data.list].length }}
      .flex-auto
      card-date(:date="item.lastModified")
    .text-md.mt-4.mb-2.font-normal(v-if="item.subtitle") {{ item.subtitle }}
    .text-xl.font-bold.rounded-xl.text-orange-800.p-2.mt-4(class="dark:text-orange-300",v-if="item.data.price") {{ item.data.price }}
  .art(v-if="item.data.art", :style="{ backgroundImage: 'url(' + '/art/' + item.data.art + ')' }",) 
</template>

<script setup>
import { useData } from 'vitepress'
const { theme } = useData()
const props = defineProps({
  item: Object,
  i: Number
});
</script>

<style lang="postcss" scoped>
a {
  @apply my-4 flex flex-wrap rounded shadow-sm;
  transition: box-shadow color 100ms ease-in-out;
}

.info {
  @apply flex flex-col p-4 w-full;
  flex: 10 1 300px;
}

.art {
  @apply bg-cover bg-center self-stretch min-h-8em;
  filter: saturate(10%) opacity(70%);
  transition: all 200ms ease-in-out;
  flex: 1 1 100px;
}

a:hover .art {
  filter: saturate(50%);
}

a:hover {
  text-decoration: none;
}
</style>