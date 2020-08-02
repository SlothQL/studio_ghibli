<template>
  <div v-if="film">
      <h3>{{film.title}}</h3>
      <p>{{film.description}}</p>
      <p>Released {{film.release_date}}</p>
  </div>
</template>

<script>

export default {
    name: 'film-detail',
    props: ['film']
}
</script>

<style scoped>
</style>