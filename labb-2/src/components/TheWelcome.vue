<script setup>
import { ref } from "vue";

let userInput = ref();
let descInput = ref();

let posts = ref([]);

const newPost = ref({
  id: "",
  postName: userInput,
  description: descInput,
});

const addPost = () => {
  createId();
  posts.value.push({ ...newPost.value });
};

const createId = () => {
  let date = new Date();
  newPost.value.id = date.getTime();
};
</script>

<template>
  <section class="dayContainer">
    <article>
      <h2 class="day">Monday</h2>
      <ul>
        <li><input v-model="userInput" placeholder="Post name" /></li>
        <li><input v-model="descInput" placeholder="Describe post" /></li>
        <button @click="addPost">Add post</button>
        <li v-for="(post, id) in posts" :key="id">{{ post }}</li>
      </ul>
    </article>
    <article><h2 class="day">Tuesday</h2></article>
    <article><h2 class="day">Wednesday</h2></article>
    <article><h2 class="day">Thursday</h2></article>
    <article><h2 class="day">Friday</h2></article>
    <article><h2 class="day">Saturday</h2></article>
    <article><h2 class="day">Sunday</h2></article>
  </section>
</template>

<style scoped>
.day {
  text-decoration: underline;
}

.dayContainer {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-around;
}

li {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

ul {
  margin: 0;
  padding: 0;
}
</style>
