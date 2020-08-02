<template>
  <div>
    <div class="header">
    <h1>WELCOME TO STUDIO GHIBLI</h1>
    </div>
    <film-list :films='films'></film-list>
    <film-detail :film="selectedFilm" ></film-detail>
    <characters :characters="foundCharacters"></characters>
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
      console.log('filmApi', filmApi);
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
    background-image: url('./assets/totoro_night.jpg');
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
    font-family: 'Inter', sans-serif;
  }

  .header {
    text-align: center;
    color: white;
    text-shadow: -1px -1px 0 rgb(8, 48, 75), 1px -1px 0 rgb(8, 48, 75), -1px 1px 0 rgb(8, 48, 75), 1px 1px 0 rgb(8, 48, 75);
  }
</style>