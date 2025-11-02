<script setup>
import IntroView from './components/IntroView.vue'
import PortfolioView from './components/PortfolioView.vue'
</script>

<template>
  <header>
    <img alt="" class="logo" src="./assets/dzimo-header.png" width="125" height="125" style="border-radius: 50%; margin-bottom: 1rem;" />
    <div class="wrapper">
      <IntroView msg="Mohamed-Nazim BELABED" />
    </div>
  </header>

  <main>
    <PortfolioView />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    flex-direction: column;
    align-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    font-size: 0.8rem;
  }
}
</style>
