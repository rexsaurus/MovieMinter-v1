<template>
  <nav>
    <ul class="nav-list">
      <li class="nav-item" v-for="link in navLinks" :key="link.text" @click="handleNavClick(link)">
        <!-- Check if the link text is 'Connect' -->
        <template v-if="link.text === 'Connect'">
          <!-- Use the Web3Modal button component for the 'Connect' link -->
          <w3m-button class="nav-link connect-button" />
        </template>
        <!-- For all other links, use the regular router-link -->
        <router-link v-else :to="link.to" class="nav-link">
          {{ link.text }}
        </router-link>
      </li>
    </ul>
    <!-- Popup Component -->
    <popup-component v-if="showPopup" :title="popupTitle" :text="popupText" @close="showPopup = false"></popup-component>
  </nav>
</template>

<script>

  import { createWeb3Modal, defaultWagmiConfig } from '@web3modal/wagmi/vue'
  import { mainnet, arbitrum } from 'viem/chains'
  import Popup from './Popup.vue'; // Import your popup component

  export default {
    name: 'NavBar',
    components: {
      'popup-component': Popup
    },
    data() {
      return {
        navLinks: [
          { text: 'How it works', to: '/how-it-works', popupTitle: 'How It Works', popupText: 'Movie Minter works by allowing users to donate their GPU to mint segments of a Generative AI movie. A director or artist submits a set of scenes, stills or prompts and the end user can volunteer to mint these segments using their GPU. As a reward, the user gets to own that clip, stored in their wallet as an NFT. When the final movie is assembled after all the pieces are minted, users who helped create the movie can get royalties whenever the full movie is viewed.' },
          { text: 'Script', to: '/script', popupTitle: 'Script', popupText: 'This is an example script about a ninja who slays a dragon in a far away mythical kingdom of cherry blossom castles.' },
          { text: 'Director', to: '/director', popupTitle: 'Director', popupText: 'Details about the director. For the purposes of this example, the director is Rex St. John.' },
          { text: 'Prompt', to: '/prompt', popupTitle: 'Prompt', popupText: 'Details about the prompts being used as the background to each image will go here. These might include details about LoRas, model checkpoints and negative prompts which are used per scene. A movie might have a cinematographer who sets all these.' },
          { text: 'Connect', to: '/connect' }, // No popup for Connect
        ],
        showPopup: false,
        popupTitle: '',
        popupText: '',
      };
    },
    methods: {
      handleNavClick(link) {
        if (link.text !== 'Connect') {
          this.popupTitle = link.popupTitle;
          this.popupText = link.popupText;
          this.showPopup = true;
        }
      }
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
    display: flex;
    justify-content: space-between; /* This will space out the navbar items */
    align-items: center; /* Aligns items vertically */
    list-style: none;
    padding: 0;
    margin: 0;
    /* Remove flex-grow: 1; since we are using space-between */
  }

  .nav-item {
    padding: 0.5rem 1rem; /* Provide padding for clickable area */
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
      border: none;
  }

  /* Hover state for the connect button */
  .connect-button:hover {
      /* Define styles for hover state here */
  }

  @media (max-width: 768px) {
    .nav-list {
      flex-direction: column; /* Stack items vertically */
      align-items: center; /* Center items horizontally */
    }

    .nav-item {
      margin-bottom: 0.5rem; /* Add space between stacked items */
    }
  }

</style>
