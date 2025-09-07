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
  computed: {
    renderPage() {},
  },
  created() {
    this.fetchPokemon()
  },
}
</script>

<template>
  <h1>Pages</h1>

  <div>
    <span style="margin-right: 20px">Users</span>
    <span>Todos</span>
    <span>Users</span>
  </div>

  <component is="renderPage" />

  <h1>Pokemon</h1>
  <pre>
    {{ pokedex }}
  </pre>
  <button @click="fetchPokemon">Fetch Pokemon</button>
</template>
