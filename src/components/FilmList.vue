<template>
  <div class="wrapper">
      <h2 class="list-headline">Explore our movies</h2>
      <ul class="list">
            <list-item class="item" v-for="film in films" :film="film" :key="film.id" v-bind:value="film"></list-item>
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
    .list {
        list-style: none;
        padding: 10px;
        display: flex;
        flex-wrap: wrap;
    }

    .item {
        margin-left: 40px;
        margin-bottom: 20px;
        width: 115px;
    }

    .list-headline {
        margin-left: 50px;
        font-size: 32px;
    }
</style>