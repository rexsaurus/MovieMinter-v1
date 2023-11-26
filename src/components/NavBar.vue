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
      ],
    };
  },
};
</script>

<style scoped>
.nav-list {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
}

.nav-item {
  margin-right: 1rem;
}

.nav-link {
  text-decoration: none;
  color: #333;
  padding: 0.5rem 1rem;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #42b983;
}
</style>
