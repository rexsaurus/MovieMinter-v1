<template>
  <button @click="connectWallet">Connect</button>
</template>

<script>
import Web3 from 'web3';

export default {
  methods: {
    async connectWallet() {
      if (window.ethereum) {
        try {
          await window.ethereum.request({ method: 'eth_requestAccounts' });
          this.web3 = new Web3(window.ethereum);
        } catch (error) {
          console.error('User denied account access');
        }
      } else {
        console.log('Non-Ethereum browser detected. You should consider trying MetaMask!');
      }
    }
  }
}
</script>
