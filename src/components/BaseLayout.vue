<template>
  <div class="wrapper">
    <div class="sidebar">
      <slot name="sidebar">Aside</slot>
    </div>
    <div class="content">
      <slot name="content">Main Content</slot>
    </div>
  </div>
  <footer class="footer">Footer</footer>
</template>

<style>
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  width: 100%;
}

.sidebar {
  border: 1px solid red;
}

.content {
  border: 1px solid blue;
  grid-column-start: 2;
  grid-column-end: 4;
}
</style>
