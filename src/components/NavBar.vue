<template>
  <nav>
    <ul class="nav-list">
      <li class="nav-item" v-for="link in navLinks" :key="link.text">
        <router-link :to="link.to" class="nav-link">{{ link.text }}</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      navLinks: [
        { text: 'How it works', to: '/how-it-works' },
        { text: 'Script', to: '/script' },
        { text: 'Director', to: '/director' },
        { text: 'Prompt', to: '/prompt' },
        { text: 'Connect', to: '/connect' },
      ],
    };
  },
};
</script>

<style scoped>
  header {
    /* Assuming you have a header tag */
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }


  .nav-list {
    list-style: none;
    display: flex;
    margin: 0;
    padding: 0;
    flex-grow: 1; /* Added to push the logo and nav items to opposite ends */
    justify-content: flex-end; /* Align nav items to the right */
  }

  .nav-item {
    margin-right: 1rem;
  }

  .nav-link {
    text-decoration: none;
    color: white;
    padding: 0.5rem 1rem;
    border: 1px solid white;
    transition: color 0.3s ease;
    white-space: nowrap; /* Prevent text wrapping */
  }


  .nav-link:hover {
    color: #42b983;
    border-color: #42b983; /* Change border color on hover */
  }

</style>
