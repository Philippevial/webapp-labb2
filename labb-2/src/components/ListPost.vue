<script setup>
const props = defineProps({
  post: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <h4
    :class="{
      food: post.choice === 'food',
      chore: post.choice === 'chore',
      activity: post.choice === 'activity',
    }"
  >
    {{ post.postName }}
    <button class="deleteBtn" @click="$emit('deletePost', post)">
      <img src="./icons/buttons/trash-solid.svg" alt="" />
    </button>
  </h4>
</template>

<style scoped>
.food {
  border-style: solid;
  border-color: crimson;
  color: green;
}

.chore {
  border-style: solid;
  color: blue;
}

.activity {
  border-style: solid;
  color: red;
}

img {
  width: 10px;
}

.deleteBtn {
  padding: 0.25rem;
}
</style>
