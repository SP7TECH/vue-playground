<script>
export default {
  props: {
    label: String,
  },
}
</script>

<template>
  <button>
    <slot>Submit</slot>
  </button>
</template>
