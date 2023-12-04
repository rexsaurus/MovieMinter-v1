<script setup>
import NavBar from './components/NavBar.vue'
import MovieGrid from './components/MovieGrid.vue'
import WalletConnector from './components/WalletConnector.vue'
</script>

<template>
  <header>
    <img alt="Movie Minter" class="logo" src="./assets/minter.png" width="125" height="125" />
    <NavBar />
  </header>

  <main>
    <MovieGrid />
  </main>

  <footer>© Taroko Research 2024</footer>
</template>

<style scoped>
  header {
    line-height: 1.5;
    display: flex;
    justify-content: flex-start; /* Align items to the left */
    align-items: center;
  }

  .logo {
    display: block;
    margin-right: auto; /* This will push everything else to the right */
  }

  /* Assuming NavBar is a flex container, you may need to reset its margins */
  .nav-bar {
    margin-left: 0; /* Reset any left margin applied by the NavBar component */
  }

  @media (min-width: 1024px) {
    .logo {
      /* Keep the margin-right for the logo if you need spacing between logo and NavBar */
      margin-right: 2rem; /* Adjust as needed */
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
  footer {
    text-align: center;
    color:white;
  }
  

</style>
