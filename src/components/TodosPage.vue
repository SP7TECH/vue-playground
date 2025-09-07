<script>
export default {
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    async fetchTodos() {
      this.todos = await fetch('https://jsonplaceholder.typicode.com/todos').then((res) =>
        res.json(),
      )
    },
  },
  mounted() {
    this.fetchTodos()
  },
}
</script>

<template>
  <h1>Todos</h1>

  <ul>
    <li v-for="todo in todos">
      <input type="checkbox" :checked="todo.completed"></input>
      {{ todo.title }}
    </li>
  </ul>
</template>
