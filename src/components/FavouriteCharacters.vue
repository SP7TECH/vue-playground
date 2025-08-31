<script>
export default {
  props: {
    favourites: {
      type: Array,
      required: true,
    },
  },
}
</script>

<template>
  <h3>Favourite Characters</h3>

  <ul v-if="favourites.length">
    <li v-for="character in favourites">{{ character }}</li>
  </ul>
  <p v-else>No favourite characters found!</p>
</template>
