<script setup>
import { ref } from "vue";

defineEmits(["addPost"]);

const userInput = ref();
const checkedDays = ref([]);
const todoOptions = ref("");

const newPost = ref({
  id: "",
  postName: userInput,
  days: checkedDays,
  choice: todoOptions,
});

const createId = () => {
  let date = new Date();
  return date.getTime();
};
</script>

<template>
  <section>
    <input v-model="userInput" placeholder="Your Todo" />
  </section>
  <section>
    <select v-model="todoOptions">
      <option disabled value="">Select Todo option</option>
      <option value="food" id="food">Food</option>
      <option value="chore" id="chore">Chore</option>
      <option value="activity" id="activity">Activity</option>
    </select>
  </section>

  <section>
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

    <button
      @click="
        $emit('addPost', {
          id: createId(),
          postName: userInput,
          days: checkedDays,
          choice: todoOptions,
        })
      "
    >
      Add post
    </button>
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
