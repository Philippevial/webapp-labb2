<script setup>
import { ref } from "vue";
import FormComp from "./FormComp.vue";
import ListPost from "./ListPost.vue";

const posts = ref([]);

const createId = () => {
  let date = new Date();
  return date.getTime();
};

const addPost = (newPost) => {
  newPost.id = createId();
  posts.value.push({ ...newPost });
};

const filterList = (filterDay) => {
  return posts.value.filter((post) =>
    post.days.find((day) => day === filterDay)
  );
};
</script>

<template>
  <FormComp @addPost="addPost" />

  <section class="dayContainer">
    <article>
      <h2 class="day">Monday</h2>
      <li v-for="(post, id) in filterList('monday')" :key="id">
        <ListPost :post="post" />
      </li>
    </article>
    <article>
      <h2 class="day">Tuesday</h2>
      <ul>
        <li v-for="(post, id) in filterList('tuesday')" :key="id">
          <ListPost :post="post" />
        </li>
      </ul>
    </article>
    <article>
      <h2 class="day">Wednesday</h2>
      <ul>
        <li v-for="(post, id) in filterList('wednesday')" :key="id">
          <ListPost :post="post" />
        </li>
      </ul>
    </article>
    <article>
      <h2 class="day">Thursday</h2>
      <ul>
        <li v-for="(post, id) in filterList('thursday')" :key="id">
          <ListPost :post="post" />
        </li>
      </ul>
    </article>
    <article>
      <h2 class="day">Friday</h2>
      <ul>
        <li v-for="(post, id) in filterList('friday')" :key="id">
          <ListPost :post="post" />
        </li>
      </ul>
    </article>
    <article>
      <h2 class="day">Saturday</h2>
      <ul>
        <li v-for="(post, id) in filterList('saturday')" :key="id">
          <ListPost :post="post" />
        </li>
      </ul>
    </article>
    <article>
      <h2 class="day">Sunday</h2>
      <ul>
        <li v-for="(post, id) in filterList('sunday')" :key="id">
          <ListPost :post="post" />
        </li>
      </ul>
    </article>
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
