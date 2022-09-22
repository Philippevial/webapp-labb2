<script setup>
const props = defineProps({
  post: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <h5
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
  </h5>
</template>

<style scoped>
.food {
  color: rgb(125, 17, 17);
}

.chore {
  color: rgb(17, 156, 47);
}

.activity {
  color: rgb(73, 14, 191);
}

img {
  width: 10px;
}

.deleteBtn {
  padding: 0.25rem;
}
</style>
