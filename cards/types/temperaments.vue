<template lang="pug">

.grid.grid-cols-1.gap-4.my-10(class="xs:grid-cols-2")
  .cell.bg-pink-100(class="dark:bg-pink-800")
    .text-4xl 😝
    h4 Сангвиник
    h5 Влияющий интроверт
    h5 (активный — внутри)
    p Реализует свои желания, преодолевает препятствия, достигает цели. Игнорирует чужую точку зрения и смену отбстоятельств.
  .cell.bg-amber-100(class="dark:bg-amber-800") 
    .text-4xl 😃
    h4 Холерик
    h5 Влияющий экстраверт
    h5 (активный — снаружи)
    p Стремится находиться в центре внимания поклонников. Харизматичен, коммуникабелен, не терпит критики.
  .cell.bg-light-blue-100(class="dark:bg-blue-800") 
    .text-4xl 🤔
    h4 Флегматик
    h5 Воспринимающий интроверт
    h5 (пассивный — внутри)
    p Боится потерять то, что имеет. Стремится к спокойствию, стабильности. Самостоятелен. Автономен. Сам себе на уме.
  .cell.bg-green-100(class="dark:bg-green-800")
    .text-4xl 🙄
    h4 Меланхолик
    h5 Воспринимающий экстраверт
    h5 (пассивный — снаружи)
    p Следует за авторитетом и лидером. Склонен к самопожертвованию. Вдумчивый, внимательный, поддерживающий.
  
</template>

<script  setup>
import { useStorage } from '@vueuse/core'

const icons = useStorage('show-icons', true);

</script>

<style lang="postcss" scoped>
.cell {
  @apply p-6 shadow rounded;
}
h4 {
  @apply mt-2 mb-4 text-xl;
}

h5 {
  @apply mb-2;
}

p {
  @apply text-lg m-0;
}
</style>