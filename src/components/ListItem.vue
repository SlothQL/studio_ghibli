<template>
  <div>
      <li v-on:click="handleClick">{{film.title}}</li>
      <img class="img" :src="require(`../assets/films/${film.title.replace(/\s/g, '-')}.jpg`)" alt="Image of movie"/>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'list-item',
    props: ['film'],
    methods: {
        handleClick() {
            eventBus.$emit('film-selected', this.film)
        }
    }
}
</script>

<style scoped>
    .img {
        width: 150px;
    }
</style>