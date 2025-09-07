<script>
import PokedexPage from './components/PokedexPage.vue'
import TodosPage from './components/TodosPage.vue'
import UsersPage from './components/UsersPage.vue'

export default {
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
