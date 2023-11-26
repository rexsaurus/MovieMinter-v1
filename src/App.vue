<script setup>
import NavBar from './components/NavBar.vue'
import MovieGrid from './components/MovieGrid.vue'
import WalletConnector from './components/WalletConnector.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <NavBar />
  </header>

  <main>
    <WalletConnector />
    <MovieGrid />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem var(--section-gap);
}

.logo {
  display: block;
}

@media (min-width: 1024px) {
  .logo {
    margin-right: 2rem;
  }

  header {
    padding-right: calc(var(--section-gap) / 2);
  }

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
