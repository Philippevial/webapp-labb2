<script setup>
import { ref } from "vue";

const emit = defineEmits(["addPost"]);

const userInput = ref();
const checkedDays = ref([]);

const weekDays = [
  "monday",
  "tuesday",
  "wednesday",
  "thursday",
  "friday",
  "saturday",
  "sunday",
];

const todoOptions = ref("");
const inputError = ref(false);

const createId = () => {
  let date = new Date();
  return date.getTime();
};

const submitInput = () => {
  const days = [...checkedDays.value];
  if (
    (userInput.value || userInput.value === 0) &&
    checkedDays.value &&
    todoOptions.value
  ) {
    inputError.value = false;
    emit("addPost", {
      id: createId(),
      postName: userInput.value,
      days: days,
      choice: todoOptions.value,
    });
  } else {
    inputError.value = true;
  }
};

const addDay = (weekDay) => {
  checkedDays.value.includes(weekDay)
    ? (checkedDays.value = checkedDays.value.filter((day) => day !== weekDay))
    : checkedDays.value.push(weekDay);
};
</script>

<template>
  <section class="formContainer">
    <h3>Add a new todo below!</h3>
    <p v-if="inputError">Your todo is missing input, try again!</p>
    <p v-else></p>
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
        <li v-for="weekDay in weekDays" :key="weekDay">
          <input type="checkbox" @input="addDay(weekDay)" />

          <label>{{
            weekDay.charAt(0).toUpperCase() + weekDay.slice(1)
          }}</label>
        </li>
      </ul>
    </article>

    <article>
      <button class="addBtn" @click="submitInput">Add post</button>
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
  margin-top: 5px;
  padding: 6px;
}

.inputContainer {
  display: flex;
  flex-direction: column;
}

.inputField {
  width: 100%;
}

@media only screen and (max-width: 600px) {
  .formContainer {
    display: flex;
    flex-direction: column;
    width: 100%;
    position: relative;
    padding: 0;
  }

  .checkBoxContainer {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    flex-wrap: nowrap;
    padding: 7px;
  }

  .inputContainer {
    display: flex;
    flex-direction: column;
    padding: 7px;
  }

  .inputField {
    width: 90%;
  }
}

@media only screen and (min-width: 601px) and (max-width: 940px) {
  .formContainer {
    background-color: #816797;
    display: flex;
    width: 100%;
    position: relative;
    border-radius: 8px;
    flex-direction: column;
    padding: 0;
  }

  .inputField {
    width: 90%;
  }

  .checkBoxContainer {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    flex-wrap: nowrap;
    padding: 7px;
  }

  .inputContainer {
    display: flex;
    flex-direction: column;
    padding: 7px;
  }
}
</style>
