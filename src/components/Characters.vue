<template>
  <div v-if="characters.length > 0">
        <div class="characters">
            <h3>Characters</h3>
            <ul class="character-list">
                <li v-for="(character, index) in characters" :character="character" :key="index">{{character.name}}</li>
            </ul>
        </div>
  </div>
</template>

<script>

export default {
    name: 'film-detail',
    props: ['characters']
}
</script>

<style scoped>
.characters {
    margin-left: 50px;
}

.character-list {
    list-style: square;
}
</style>