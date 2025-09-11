<script setup>
import { runsInOdiReactive } from '@/composables/runsStore'
import { ref } from 'vue'

const pokedex = ref([])
async function fetchPokemon() {
  pokedex.value = await fetch('https://pokeapi.co/api/v2/pokemon?limit=5').then((response) =>
    response.json(),
  )
}
fetchPokemon()
</script>

<template>
  <h1>Pokemon</h1>

  <h2>Runs Scored</h2>
  <h3>Runs by Virat: {{ runsInOdiReactive }}</h3>

  <pre>
    {{ pokedex }}
  </pre>
  <!-- <button @click="fetchPokemon">Fetch Pokemon</button> -->
</template>
