<template>
  <div>
    <h1>Welcome to Studio Ghibli</h1>
    <h3>Explore all our movies</h3>
    <film-list :films='films'></film-list>
    <film-detail :film="selectedFilm"></film-detail>
  </div>
</template>

<script>
import FilmList from './components/FilmList.vue';
import FilmDetail from './components/FilmDetail.vue';
import { eventBus } from '@/main.js';

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(data => this.films = data)
    .catch(err => console.log(err))

    eventBus.$on('film-selected', (film) =>{
      this.selectedFilm = film;
    })
  },

  components: {
    'film-list': FilmList,
    'film-detail': FilmDetail
  }
}
</script>

<style>

</style>