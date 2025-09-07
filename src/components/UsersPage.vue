<script>
export default {
  data() {
    return {
      users: [],
    }
  },
  methods: {
    async fetchUsers() {
      this.users = await fetch('https://jsonplaceholder.typicode.com/users').then((res) =>
        res.json(),
      )
    },
  },
  mounted() {
    return this.fetchUsers()
  },
}
</script>

<template>
  <h1>Users</h1>

  <ul>
    <li v-for="user in users">{{ user.name }} - {{ user.email }}</li>
  </ul>
</template>
