<script setup>
import { RouterLink, RouterView } from "vue-router";
import MyHeader from "./components/MyHeader.vue";
import MyMenu from "./components/MyMenu.vue";
import MyFooter from "./components/MyFooter.vue";
</script>

<template>
  <header>
    <div>
      <MyHeader msg="Just Todo it" />
      <MyMenu />
    </div>
  </header>
  <body>
    <RouterView />
  </body>
  <MyFooter />
</template>

<style scoped></style>
