<script setup>
import { ref } from "vue";

defineEmits(["addPost"]);

const userInput = ref();
const checkedDays = ref([]);
const todoOptions = ref("");

const createId = () => {
  let date = new Date();
  return date.getTime();
};
</script>

<template>
  <section class="formContainer">
    <h3>Add a new todo below!</h3>
    <section class="inputContainer">
      <article>
        <input class="inputField" v-model="userInput" placeholder="Your Todo" />
      </article>
      <article>
        <select v-model="todoOptions">
          <option disabled value="">Select Todo option</option>
          <option value="food" id="food">Food</option>
          <option value="chore" id="chore">Chore</option>
          <option value="activity" id="activity">Activity</option>
        </select>
      </article>
    </section>
    <article class="checkBoxContainer">
      <ul>
        <li>
          <input
            type="checkbox"
            id="monday"
            value="monday"
            v-model="checkedDays"
          />
          <label for="monday">Monday</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="tuesday"
            value="tuesday"
            v-model="checkedDays"
          />
          <label for="tuesday">Tuesday</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="wednesday"
            value="wednesday"
            v-model="checkedDays"
          />
          <label for="tuesday">Wednesday</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="thursday"
            value="thursday"
            v-model="checkedDays"
          />
          <label for="thursday">Thursday</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="friday"
            value="friday"
            v-model="checkedDays"
          />
          <label for="friday">Friday</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="saturday"
            value="saturday"
            v-model="checkedDays"
          />
          <label for="saturday">Saturday</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="sunday"
            value="sunday"
            v-model="checkedDays"
          />
          <label for="sunday">Sunday</label>
        </li>
      </ul>
    </article>

    <article>
      <button
        class="addBtn"
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
    </article>
  </section>
</template>

<style scoped>
li {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

ul {
  margin: 0;
  padding: 0;
}

.formContainer {
  background-color: #816797;
  display: flex;
  width: 15%;
  flex-wrap: wrap;
  float: left;
  position: fixed;
  padding: 1rem;
  border-radius: 8px;
}

.checkBoxContainer {
  display: flex;
  flex-wrap: nowrap;
  align-items: center;
}

.addBtn {
  padding: 6px;
}

.inputContainer {
  display: flex;
  flex-direction: column;
}

.inputField {
  width: 100%;
}
</style>
