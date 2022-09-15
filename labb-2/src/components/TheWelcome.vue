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
  <section class="dayContainer">
    <article v-for="weekDay in weekDays">
      <h2 class="dayHead">
        {{ weekDay.charAt(0).toUpperCase() + weekDay.slice(1) }}
      </h2>
      <li class="day" v-for="(post, id) in filterList(weekDay)" :key="id">
        <ListPost :post="post" @deletePost="deletePost" />
      </li>
    </article>
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
