<template>
  <div>
      <li>{{film.title}}</li>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'list-item',
    props: ['film']
}
</script>

<style scoped>

</style>