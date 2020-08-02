<template>
  <div>
    <div class="header">
      <h1 class="headline">WELCOME TO STUDIO GHIBLI</h1>
    </div>
      <div class="display">
      <film-list :films='films'></film-list>
      <div class="app-details">
        <film-detail :film="selectedFilm" ></film-detail>
        <characters :characters="foundCharacters"></characters>
      </div>
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
    background-color: goldenrod;
    background-image: url('./assets/totoro.jpeg');
    background-repeat: no-repeat;
    background-size: 100% 400px;
  }

  .header {
    height: 400px;
    text-align: center;
    margin-top: -15px;
  }

  .headline {
    color: goldenrod;
    font-size: 56px;
  }

  .app-details {
    width: 58%;
    margin-bottom: 30px;
    margin-top: 50px;
  }

  .display {
    margin-top: 50px;
  }
</style>