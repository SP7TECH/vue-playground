<script>
import BaseButton from './components/BaseButton.vue'
import BaseLayout from './components/BaseLayout.vue'
import CharacterList from './components/CharacterList.vue'
import FavouriteCharacters from './components/FavouriteCharacters.vue'

export default {
  data() {
    return {
      movieName: 'Mission Impossible',
      newCharacter: {
        name: '',
        age: 0,
      },
      characters: [
        { name: 'Ethan Hunt', age: 59 },
        { name: 'Luther', age: 52 },
        { name: 'Benji', age: 49 },
        { name: 'Julia', age: 42 },
        { name: 'Ilsa', age: 40 },
      ],
      favourites: [],
      // characters: [],
    }
  },
  computed: {
    calcAverageAge() {
      const totalAge = this.characters.reduce((prev, curr) => prev + Number(curr.age), 0)
      return totalAge / this.characters.length
    },
  },
  methods: {
    addCharacter() {
      this.characters.push(this.newCharacter)
      this.newCharacter = { name: '', age: 0 }
    },
    handleCharacterNameChange(e) {
      this.newCharacter.name = e.target.value
    },
    handleCharacterAgeChange(e) {
      this.newCharacter.age = e.target.value
    },
    markAsFavourite(payload) {
      this.favourites.push(payload.name)
    },
  },
  components: {
    FavouriteCharacters,
    CharacterList,
    BaseButton,
    BaseLayout,
  },
}
</script>

<template>
  <h1>Exercises</h1>

  <BaseButton>Cancel</BaseButton>

  <h2>{{ movieName }}</h2>

  <h3>Add Characters</h3>

  <div>
    <label for="character">Character Name</label>
    <input type="text" v-bind:value="newCharacter.name" v-on:input="handleCharacterNameChange" />
    <input type="number" v-bind:value="newCharacter.age" v-on:input="handleCharacterAgeChange" />
  </div>

  <button v-on:click="addCharacter">Add Character</button>

  <CharacterList :characters="characters" @favourite="markAsFavourite" />

  <h3>Average Age of Characters: {{ calcAverageAge }}</h3>

  <p>
    <span v-for="(character, index) in characters"
      >{{ character.name }}{{ index === characters.length - 1 ? '' : ', ' }}</span
    >
  </p>

  <hr />
  <FavouriteCharacters :favourites="favourites" />

  <BaseLayout>
    <template v-slot:sidebar>Side Bar</template>

    <template v-slot:content>Main Content</template>
  </BaseLayout>
</template>
