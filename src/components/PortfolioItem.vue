<template>
  <div class="portfolio-item" @click="$emit('open')">
    <img :src="image" alt="" class="portfolio-image" />
    <h3>{{ title }}</h3>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  image: String,
});
</script>

<style scoped>
.portfolio-item {
  cursor: pointer;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  overflow: hidden;
  text-align: center;
  transition: transform 0.2s;
}

.portfolio-item:hover {
  transform: scale(1.03);
}

.portfolio-image {
  width: 100%;
  height: 150px;
  object-fit: cover;
}

h3 {
  margin: 0.5rem 0;
}
</style>
