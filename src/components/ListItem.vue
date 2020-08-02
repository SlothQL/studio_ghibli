<template>
  <div>
        <img v-on:click="handleClick" class="img" :src="require(`../assets/films/${film.title.replace(/\s/g, '-')}.jpg`)" alt="Image of movie"/>
        <li class="title">{{film.title}}</li>
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
        height: 150px;
        width: 115px;
    }

    .title {
        font-size: 12px;
        overflow-wrap: break-word;
    }
</style>