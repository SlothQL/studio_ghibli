<template>
  <div>
    <div class="header">
      <h1 class="banner">WELCOME TO STUDIO GHIBLI</h1>
    </div>
      <film-list :films='films'></film-list>
      <div class="details">
      <film-detail :film="selectedFilm" ></film-detail>
      <characters :characters="foundCharacters"></characters>
      </div>
  </div>
</template>

<script>
import FilmList from './components/FilmList.vue';
import FilmDetail from './components/FilmDetail.vue';
import Characters from './components/Characters.vue';
import { eventBus } from '@/main.js';

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null,
      characters: [],
      foundCharacters: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(data => this.films = data)
    .catch(err => console.log(err))

    fetch('https://ghibliapi.herokuapp.com/people/')
    .then(res => res.json())
    .then(data => this.characters = data)
    .catch(err => console.log(err))

    eventBus.$on('film-selected', (film) =>{
      this.selectedFilm = film;
      this.findCharacters();
    })
  },

  methods: {
    findCharacters() {
      const filmApi = `https://ghibliapi.herokuapp.com/films/${this.selectedFilm.id}`;
      this.foundCharacters = this.characters.filter(character => character.films[0] === filmApi);
      return this.foundCharacters;
    }
  },

  components: {
    'film-list': FilmList,
    'film-detail': FilmDetail,
    'characters': Characters
  }
}
</script>

<style>
  body {
    font-family: 'Inter', sans-serif;
  }
</style>