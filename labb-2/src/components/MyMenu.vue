<script setup></script>

<template>
  <nav class="menu">
    <RouterLink to="/"><h3>Home</h3></RouterLink>
    <RouterLink to="/about"><h3>About</h3></RouterLink>
  </nav>
</template>

<style scoped>
.menu {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-evenly;
  margin-bottom: 1.5rem;
}
</style>
