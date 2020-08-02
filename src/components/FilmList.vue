<template>
  <div>
      <ul>
          <li v-for="film in films" :film="film" :key="film.id" v-bind:value="film"></li>
      </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    name: 'film-list',
    props: ['films'],
    components: {
        'list-item': ListItem
    }
}
</script>

<style scoped>

</style>