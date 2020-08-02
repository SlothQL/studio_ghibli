<template>
  <div v-if="characters.length > 0">
        <div>
            <h3>Characters</h3>
            <ul>
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
</style>