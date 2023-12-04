<template>
  <div class="scene-detail-container">
    <div class="scene-detail-header">
      <h2>Scene Detail</h2>
      <button class="close-button" @click="closeForm">X</button>
    </div>
    <form @submit.prevent="mintScene">
      <div class="form-group">
        <label for="scene-description">Scene Description</label>
        <textarea id="scene-description" v-model="scene.description" rows="3"></textarea>
      </div>
      <div class="form-group">
        <label for="characters">Characters</label>
        <input id="characters" v-model="scene.characters" type="text">
      </div>
      <div class="form-group">
        <label for="prompt">Prompt</label>
        <input id="prompt" v-model="scene.prompt" type="text">
      </div>
      <div class="form-group half-width">
        <label for="est-value">Est. Value</label>
        <input id="est-value" v-model="scene.estValue" type="text">
      </div>
      <div class="form-group half-width">
        <label for="est-mint-time">Est. Mint Time</label>
        <input id="est-mint-time" v-model="scene.estMintTime" type="text">
      </div>
      <div class="form-group">
        <button type="submit" class="mint-button">Mint</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      scene: {
        description: '',
        characters: '',
        prompt: '',
        estValue: '',
        estMintTime: ''
      }
    };
  },
  methods: {
    closeForm() {
      // Logic to close the form, for example, emitting an event or changing a v-if condition
      this.$emit('close');
    },
    mintScene() {
      // Logic to handle the minting of the scene
      console.log('Minting scene:', this.scene);
      // You would typically send this data to a server or blockchain transaction
    }
  }
};
</script>

<style scoped>
.scene-detail-container {
  border: 1px solid #ccc;
  padding: 1rem;
  position: relative;
  background: white;
  color: black;
  width: 400px; /* Set your desired width */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
}

.scene-detail-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.close-button {
  border: none;
  background: none;
  cursor: pointer;
  font-size: 1.5rem;
}

.form-group {
  margin-bottom: 1rem;
}

.form-group.half-width {
  display: inline-block;
  width: calc(50% - 0.5rem);
}

.mint-button {
  padding: 0.5rem 1rem;
  cursor: pointer;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  font-weight: bold;
}

/* Add additional styling as needed */
</style>
