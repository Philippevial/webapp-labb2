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
      <article class="singleDayContainer" v-for="weekDay in weekDays">
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

.singleDayContainer {
  width: 25%;
  height: 25vh;
  overflow: auto;
}
.dayContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 80%;
  padding-bottom: 0;
}

li {
  border: 1px solid black;
  margin-top: -1px; /* Prevent double borders */
  background-color: #d6d5a8;
  padding: 5px;
  text-decoration: none;
  max-width: 22vh;
  overflow: auto;
}

.container {
  display: flex;
  justify-content: space-evenly;
  margin-left: 200px;
  position: relative;
  min-height: 80vh;
}

/**Phone**/
@media only screen and (max-width: 600px) {
  .container {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin: 0;
    align-items: center;
    justify-content: center;
  }

  .day {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .singleDayContainer {
    width: 100%;
    height: 25vh;
    overflow: auto;
  }

  .dayContainer {
    display: flex;
    width: 100%;
  }
}

@media screen and (min-width: 601px) and (max-width: 940px) {
  .container {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin: 0;
    align-items: center;
    justify-content: center;
  }

  .day {
    display: flex;
    flex-wrap: nowrap;
    justify-content: space-between;
    max-width: fit-content;
  }

  .singleDayContainer {
    width: 33%;
    height: 25vh;
    overflow: auto;
  }
}
</style>
