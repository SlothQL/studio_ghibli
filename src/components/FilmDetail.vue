<template>
  <div v-if="film" class="details">
      <h2>{{film.title}}</h2>
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
    .details {
        margin-left: 50px;
        margin-top: -20px;
    }
</style>