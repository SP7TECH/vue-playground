<script>
import { reactive } from 'vue'
import PokedexPage from './components/PokedexPage.vue'
import TodosPage from './components/TodosPage.vue'
import UsersPage from './components/UsersPage.vue'
import { runsInOdiReactive } from './composables/runsStore'

export default {
  setup() {
    const playerName = 'Virat Kohli'
    const runsInOdi = 8000
    // const runsInOdiReactive = ref(8000)
    let state = reactive({
      pokemons: [],
    })

    function incrementRunBy4() {
      return runsInOdi + 4
    }

    function incrementRunBy6() {
      return (runsInOdiReactive.value += 6)
    }

    async function fetchPokemon() {
      state.pokemons = await fetch('https://pokeapi.co/api/v2/pokemon?limit=2').then((response) =>
        response.json(),
      )
    }

    return {
      playerName,
      runsInOdi,
      runsInOdiReactive,
      incrementRunBy4,
      incrementRunBy6,
      state,
      fetchPokemon,
    }
  },
  data() {
    return {
      page: 'Pokedex',
    }
  },
  computed: {
    renderPage() {
      return this.page + 'Page'
    },
  },
  components: {
    PokedexPage,
    TodosPage,
    UsersPage,
  },
  methods: {
    handlePokedexPage() {
      this.page = 'Pokedex'
    },
    handleUsersPage() {
      this.page = 'Users'
    },
    handleTodoPage() {
      this.page = 'Todos'
    },
  },
}
</script>

<template>
  <h1>Composition API</h1>

  <h3>{{ playerName }}</h3>
  <p>Runs in ODI: {{ runsInOdi }} | {{ runsInOdiReactive }}</p>
  <button @click="incrementRunBy4">Increment Run by 4</button>
  <button @click="incrementRunBy6">Increment Run by 6</button>

  <pre>{{ state.pokemons }}</pre>
  <button @click="fetchPokemon">Fetch Pokemons</button>

  <h1>Pages</h1>

  <div>
    <button class="nav-btn" @click="handlePokedexPage">Pokedex</button>
    <button class="nav-btn" @click="handleUsersPage">Users</button>
    <button class="nav-btn" @click="handleTodoPage">Todos</button>
  </div>

  <!-- <PokedexPage v-if="page === 'PokedexPage'" /> -->

  <component :is="renderPage" />
</template>

<style>
.nav-btn {
  cursor: pointer;
}

.nav-btn:not(:last-child) {
  margin-right: 20px;
}
</style>
