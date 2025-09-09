<script setup>
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
  <pre>
    {{ pokedex }}
  </pre>
  <!-- <button @click="fetchPokemon">Fetch Pokemon</button> -->
</template>
