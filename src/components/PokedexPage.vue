<script>
export default {
  data: () => ({
    pokedex: [1, 2, 3],
  }),
  methods: {
    async fetchPokemon() {
      this.pokedex = await fetch('https://pokeapi.co/api/v2/pokemon?limit=5').then((response) =>
        response.json(),
      )
    },
  },
  created() {
    this.fetchPokemon()
  },
}
</script>

<template>
  <h1>Pokemon</h1>
  <pre>
    {{ pokedex }}
  </pre>
  <button @click="fetchPokemon">Fetch Pokemon</button>
</template>
