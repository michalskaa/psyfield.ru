<template lang="pug">
.text-sm.rounded-full.py-1.px-2.flex.items-center
  mdi-watering-can.mr-1.text-lg.opacity-50.text-green-800.transition(class="dark:text-green-200")
  .flex-1.font-normal {{ elapsed }}
</template>

<script setup>
import { computed } from 'vue'
import TimeAgo from 'javascript-time-ago'

const props = defineProps({
  date: String,
});

const timeAgo = new TimeAgo('ru-RU')
const elapsed = computed(() => {
  return timeAgo.format(new Date(props.date), 'mini')
})
</script>
