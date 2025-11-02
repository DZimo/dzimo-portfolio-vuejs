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

const itemsPerPage = 4;
const currentPage = ref(1);
const selectedItem = ref(null);
const modalOpen = ref(false);

const projects = [
  { id: 1, title: 'Project 1', image: '/assets/project1.jpg', description: '...' },
  { id: 2, title: 'Project 2', image: '/assets/project2.jpg', description: '...' },
  { id: 3, title: 'Project 3', image: '/assets/project3.jpg', description: '...' },
  { id: 4, title: 'Project 4', image: '/assets/project4.jpg', description: '...' },
  { id: 5, title: 'Project 5', image: '/assets/project5.jpg', description: '...' },
  { id: 6, title: 'Project 6', image: '/assets/project6.jpg', description: '...' },
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
