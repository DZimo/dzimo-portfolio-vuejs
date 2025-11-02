<template>
  <div class="portfolio-grid">
    <PortfolioItem v-for="item in paginatedProjects" :key="item.id" :title="item.title" :image="item.image"
      @open="openModal(item)" />
  </div>

  <div class="pagination">
    <button class="btn-class-name" @click="prevPage" :disabled="currentPage === 1">
      <span>Previous</span>
      <svg xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 320 512">
        <path
          d="M310.6 233.4c12.5 12.5 12.5 32.8 0 45.3l-192 192c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L242.7 256 73.4 86.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l192 192z">
        </path>
      </svg>
    </button>

    <span style="margin: 1rem;">{{ currentPage }} / {{ totalPages }}</span>

    <button class="btn-class-name" @click="nextPage" :disabled="currentPage === totalPages">
      <span>Next</span>
      <svg xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 320 512">
        <path
          d="M310.6 233.4c12.5 12.5 12.5 32.8 0 45.3l-192 192c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L242.7 256 73.4 86.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l192 192z">
        </path>
      </svg>
    </button>
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
  { id: 1, title: 'LazyPinger, a fast MAUI C# Network detection and testing.', image: '@/src/assets/lazy_pinger_main_gui.gif', description: 'TCP/IP related network management, devices discovery, database management, UDP/TCP port server/client, CAN protcol testing.' },
  { id: 2, title: 'An automated static taint analysis tool for Android.', image: '@/src/assets/unknown.png', description: 'A tool that automates more than 15 static taint anylsis Android tools, with providing benchmarks, statistics and easy comparaison, the app is cross paltform and was written in Avalonia while followding software clean architecture principles.' },
  { id: 3, title: 'Java fault localization with tarantula', image: '@/src/assets/unknown.png', description: '...' },
  { id: 4, title: 'Unity C# 2D draw to 3D X-Y-Z Coordinates shape.', image: '@/src/assets/unknown.png', description: '...' },
  { id: 5, title: 'Java Automated Test suite generation using Simulated Annealing algorithms. ( Access upon request )', image: '@/src/assets/unknown.png', description: '...' },
  { id: 6, title: 'Unity C# Automated map spawner with safe pool and delete.', image: '@/src/assets/unknown.png', description: '...' },
  { id: 7, title: 'C++ Front end compiler for a c-style language.', image: '@/src/assets/unknown.png', description: '...' },
  { id: 8, title: 'Java Dynamic analysis tool to validate patches in Java.', image: '@/src/assets/unknown.png', description: '...' },
  { id: 9, title: '3D Version of haxball game.', image: '@/src/assets/unknown.png', description: '...' },
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

.pagination{
  margin: 1rem;
  align-items: center;
  align-content: center;
  text-align: center;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  padding: 1rem;
}

.btn-class-name {
  --color: 78, 174, 54;
  border-radius: .5em;
  transition: .3s;
  background-color: rgba(var(--color), .2);
  color: rgb(var(--color));
  fill: rgb(var(--color));
  font-family: monospace;
  font-weight: bolder;
  font-size: medium;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  cursor: pointer;
  border: 2px solid rgb(var(--color));
  box-shadow: 0 0 10px rgba(var(--color), .4);
  outline: none;
  align-items: center;
  align-self: center;
  padding: .5em 1em;
}

.btn-class-name:hover {
  box-shadow: 0 0 0 5px rgba(var(--color), .5);
}

.btn-class-name span {
  transform: scale(.8);
  transition: .3s;
}

.btn-class-name:hover span {
  transform: scale(1);
}

.btn-class-name svg {
  font-size: 0;
  transform: scale(0.5) translateX(0%) rotate(-180deg);
  transition: .3s;
}

.btn-class-name:hover svg {
  font-size: 20px;
  transform: scale(1) translateX(20%) rotate(0deg);
}

.btn-class-name:active {
  transition: 0s;
  box-shadow: 0 0 0 5px rgb(var(--color));
}
</style>
