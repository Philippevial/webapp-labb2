<script setup>
const props = defineProps({
  post: {
    type: Object,
    required: true,
  },
});

console.log(props.post.choice);
</script>

<template>
  <p
    :class="{
      food: post.choice === 'food',
      chore: post.choice === 'chore',
      activity: post.choice === 'activity',
    }"
  >
    {{ post.postName }}
    <button @click="$emit('deletePost', post)">Delete</button>
  </p>
</template>

<style scoped>
.food {
  background-color: blue;
}

.chore {
  background-color: blueviolet;
}

.activity {
  background-color: aquamarine;
}
</style>
