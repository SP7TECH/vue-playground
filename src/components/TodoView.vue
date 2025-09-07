<script>
export default {
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    async fetchTodos() {
      this.todos = await fetch('')
    },
  },
}
</script>

<template></template>
