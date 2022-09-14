<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="Mat mat" />

      <nav class="menu">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.menu {
  font-size: large;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-evenly;
  margin-bottom: 1.5rem;
  background-color: aqua;
}
</style>
