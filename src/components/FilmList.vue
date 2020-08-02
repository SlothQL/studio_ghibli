<template>
  <div class="wrapper">
      <ul class="list">
            <h2>Explore all our movies</h2>
            <div>
                <list-item v-for="film in films" :film="film" :key="film.id" v-bind:value="film"></list-item>
            </div>
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
    .wrapper {
        display: flex;
    }
    .list {
        list-style: none;
        background-color: white;
        padding: 5px;
        margin: 10px;
    }
</style>