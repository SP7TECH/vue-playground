<script>
export default {
  props: {
    characters: {
      type: Array,
    },
  },
  emits: ['favourite'],
  methods: {
    favouriteCharacter(character) {
      this.$emit('favourite', character)
    },
  },
}
</script>

<template>
  <h3>Characters</h3>
  <ul v-if="characters.length">
    <li v-for="character in characters">
      {{ character.name }}
      <button @click="favouriteCharacter(character)">Mark as favourite</button>
    </li>
  </ul>
  <p v-else>No characters found</p>
</template>
