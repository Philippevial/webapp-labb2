<script setup>
import { ref } from "vue";

let userInput = ref();
// let descInput = ref();
let checkedDays = ref([]);
const newPost = ref({
  id: "",
  postName: userInput,
  days: checkedDays,
});
</script>

<template>
  <section>
    <li><input v-model="userInput" placeholder="Post name" /></li>
    <!-- <li><input v-model="descInput" placeholder="Describe post" /></li> -->

    <input type="checkbox" id="monday" value="monday" v-model="checkedDays" />
    <label for="monday">Monday</label>

    <input type="checkbox" id="tuesday" value="tuesday" v-model="checkedDays" />
    <label for="tuesday">Tuesday</label>

    <input
      type="checkbox"
      id="wednesday"
      value="wednesday"
      v-model="checkedDays"
    />
    <label for="tuesday">Wednesday</label>

    <input
      type="checkbox"
      id="thursday"
      value="thursday"
      v-model="checkedDays"
    />
    <label for="thursday">Thursday</label>

    <input type="checkbox" id="friday" value="friday" v-model="checkedDays" />
    <label for="friday">Friday</label>

    <input
      type="checkbox"
      id="saturday"
      value="saturday"
      v-model="checkedDays"
    />
    <label for="saturday">Saturday</label>

    <input type="checkbox" id="sunday" value="sunday" v-model="checkedDays" />
    <label for="sunday">Sunday</label>

    <button @click="$emit('addPost', newPost)">Add post</button>
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
