<template>
  <nav>
    <ul class="nav-list">
      <li class="nav-item" v-for="link in navLinks" :key="link.text">
        <router-link :to="link.to"
                     class="nav-link"
                     :class="{ 'connect-button': link.text === 'Connect' }">
          {{ link.text }}
        </router-link>
      </li>
    </ul>
  </nav>
</template>

<script>

  import { createWeb3Modal, defaultWagmiConfig } from '@web3modal/wagmi/vue'
  import { mainnet, arbitrum } from 'viem/chains'
  
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


  // 1. Get projectId at https://cloud.walletconnect.com
  const projectId = 'YOUR_PROJECT_ID'

  // 2. Create wagmiConfig
  const metadata = {
    name: 'Web3Modal',
    description: 'Web3Modal Example',
    url: 'https://web3modal.com',
    icons: ['https://avatars.githubusercontent.com/u/37784886']
  }

  const chains = [mainnet, arbitrum]
  const wagmiConfig = defaultWagmiConfig({ chains, projectId, metadata })

  // 3. Create modal
  createWeb3Modal({ wagmiConfig, projectId, chains })
  
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
    cursor: pointer; /* Changes the cursor to a pointer on hover */
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

  .connect-button {
    background-color: orange; /* Sets the background color to orange */
    color: white; /* Sets the text color to white for contrast */
    border: 1px solid orange; /* Sets the border color to match the background */
  }

  /* Hover state for the connect button */
  .connect-button:hover {
    background-color: darkorange; /* Darkens the button on hover for a visual effect */
    border-color: darkorange; /* Matches the border color to the background on hover */
  }

</style>
