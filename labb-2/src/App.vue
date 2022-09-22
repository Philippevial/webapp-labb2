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

<style scoped>
@media screen and (min-width: 601px) and (max-width: 940px) {
  body {
    margin: 0;
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-items: center;
    width: 100%;
  }
}

body {
  margin: 0;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  width: 100%;
}
</style>
