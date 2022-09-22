<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <header class="banner">
    <div class="banner-container">
      <div class="banner-text">
        <h1>{{ msg }}</h1>
      </div>
    </div>
  </header>
</template>

<style scoped>
.banner {
  height: 20vh;
  width: 100%;
  background: #51557e;
  margin-bottom: 2rem;
  border-radius: 0.25rem;
  position: relative;
}

.banner-container {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0.25rem;
}

.banner-text {
  text-align: center;
  color: #d6d5a8;
}

@media only screen and (max-width: 600px) {
  .banner {
    width: 100%;
  }

  .banner-container {
    width: 100%;
  }

  .banner-text {
    width: 100%;
  }
}
</style>
