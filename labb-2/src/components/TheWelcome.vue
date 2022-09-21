<script setup>
import { ref } from "vue";
import FormComp from "./FormComp.vue";
import ListPost from "./ListPost.vue";

const posts = ref([]);

const weekDays = [
  "monday",
  "tuesday",
  "wednesday",
  "thursday",
  "friday",
  "saturday",
  "sunday",
];

const addPost = (newPost) => {
  posts.value.push({ ...newPost });
};

const filterList = (filterDay) => {
  return posts.value.filter((post) =>
    post.days.find((day) => day === filterDay)
  );
};

const deletePost = (deletedPost) => {
  posts.value = posts.value.filter((post) => post.id !== deletedPost.id);
};
</script>

<template>
  <FormComp @addPost="addPost" />

  <section class="container">
    <section class="dayContainer">
      <article v-for="weekDay in weekDays">
        <h4 class="dayHead">
          {{ weekDay.charAt(0).toUpperCase() + weekDay.slice(1) }}
        </h4>
        <li class="day" v-for="(post, id) in filterList(weekDay)" :key="id">
          <ListPost :post="post" @deletePost="deletePost" />
        </li>
      </article>
    </section>
  </section>
</template>

<style scoped>
.dayHead {
  text-decoration: underline;
}

.day {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  max-width: fit-content;
}

.dayContainer {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-around;
  width: 80%;
  padding-bottom: 0;
}

li {
  margin: 0;
  padding: 0;
}

ul {
  margin: 0;
  padding: 0;
}

.container {
  display: flex;
  justify-content: space-evenly;
  margin-left: 200px;

  position: relative;
  min-height: 100vh;
}
</style>
