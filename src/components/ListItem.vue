<template>
  <div>
      <li>{{film.title}}</li>
  </div>
</template>

<script>
export default {
    name: 'list-item',
    props: ['film']
}
</script>

<style scoped>

</style>