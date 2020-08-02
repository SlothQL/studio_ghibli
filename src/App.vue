<template>
  <div>
    <h1>Welcome to Studio Ghibli</h1>
    <h3>Explore all our movies</h3>
    <film-list :films='films'></film-list>
  </div>
</template>

<script>
import FilmList from './components/FilmList.vue';

export default {
  name: 'app',
  data() {
    return {
      films: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(data => this.films = data)
    .catch(err => console.log(err))
  },

  components: {
    'film-list': FilmList
  }
}
</script>

<style>

</style>