<template>
  <div class="portfolio-grid">
    <PortfolioItem v-for="item in paginatedProjects" :key="item.id" :title="item.title" :image="item.image"
      @open="openModal(item)" />
  </div>

  <div class="pagination">
    <button @click="prevPage" :disabled="currentPage === 1">Previous</button>
    <span>{{ currentPage }} / {{ totalPages }}</span>
    <button @click="nextPage" :disabled="currentPage === totalPages">Next</button>
  </div>

  <PortfolioPopup v-if="modalOpen" @close="closeModal">
    <h2>{{ selectedItem?.title }}</h2>
    <img :src="selectedItem?.image" alt="" style="width: 100%; margin-bottom: 1rem;" />
    <p>{{ selectedItem?.description }}</p>
  </PortfolioPopup>
</template>

<script setup>
import { ref, computed } from 'vue';
import PortfolioItem from './PortfolioItem.vue';
import PortfolioPopup from './PortfolioPopup.vue';

const itemsPerPage = 6;
const currentPage = ref(1);  
const selectedItem = ref(null);
const modalOpen = ref(false);

const projects = [
  { id: 1, title: 'LazyPinger, a fast MAUI C# Network detection and testing.', image: '/src/assets/lazy_pinger_main_gui.gif', description: 'TCP/IP related network management, devices discovery, database management, UDP/TCP port server/client, CAN protcol testing.' },
  { id: 2, title: 'An automated static taint analysis tool for Android.', image: '/src/assets/logo.svg', description: 'A tool that automates more than 15 static taint anylsis Android tools, with providing benchmarks, statistics and easy comparaison, the app is cross paltform and was written in Avalonia while followding software clean architecture principles.' },
  { id: 3, title: 'Java fault localization with tarantula', image: '/assets/project3.jpg', description: '...' },
  { id: 4, title: 'Unity C# 2D draw to 3D X-Y-Z Coordinates shape.', image: '/assets/project4.jpg', description: '...' },
  { id: 5, title: 'Java Automated Test suite generation using Simulated Annealing algorithms. ( Access upon request )', image: '/assets/project5.jpg', description: '...' },
  { id: 6, title: 'Unity C# Automated map spawner with safe pool and delete.', image: '/assets/project6.jpg', description: '...' },
  { id: 7, title: 'C++ Front end compiler for a c-style language.', image: '/assets/project6.jpg', description: '...' },
  { id: 8, title: 'Java Dynamic analysis tool to validate patches in Java.', image: '/assets/project6.jpg', description: '...' },
  { id: 9, title: '3D Version of haxball game.', image: '/assets/project6.jpg', description: '...' },
];

const totalPages = computed(() => Math.ceil(projects.length / itemsPerPage));
const paginatedProjects = computed(() =>
  projects.slice((currentPage.value - 1) * itemsPerPage, currentPage.value * itemsPerPage)
);

const nextPage = () => {
  if (currentPage.value < totalPages.value) currentPage.value++;
};

const prevPage = () => {
  if (currentPage.value > 1) currentPage.value--;
};

const openModal = (item) => {
  selectedItem.value = item;
  modalOpen.value = true;
};

const closeModal = () => {
  selectedItem.value = null;
  modalOpen.value = false;
};
</script>

<style scoped>
.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  padding: 1rem;
}
</style>
