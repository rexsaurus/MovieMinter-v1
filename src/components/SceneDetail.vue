<template>
  <div class="scene-detail-container">
    <div class="scene-detail-header">
      <h2>{{ scene.segment }}</h2> <!-- Assuming 'segment' can be used as a scene number -->
      <button class="close-button" @click="closeForm">X</button>
    </div>
    <div class="scene-content">
      <img :src="scene.imagePath" class="scene-thumbnail" alt="Movie Scene" />
      <div class="scene-description">
        <p>In this scene, the character</p>
        <p>{{ scene.description }}</p>
        <p>Est. Processing time: {{ scene.estProcessingTime }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    scene: Object // Accept a scene object instead of just imagePath
  },
  methods: {
    closeForm() {
      // Emit an event to signal the parent component to close the detail view
      this.$emit('close');
    }
  }
};
</script>

<style scoped>
.scene-detail-container {
  /* ... styles from the original code ... */
  max-width: none; /* Allow the container to expand to fit content */
  margin: auto; /* Center the container */
}

.scene-detail-header {
  /* ... styles from the original code ... */
  padding: 0.5rem 1rem; /* Add padding around the header */
  background-color: #f2f2f2; /* Light grey background for the header */
}

/* Rest of the styles from the original code */

/* New style for the mint button to match the image */
.mint-button {
  /* ... styles from the original code ... */
  width: 100%; /* Make the button full width */
  font-size: 1.25rem; /* Increase the font size */
}


  .scene-content {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .scene-thumbnail {
    max-width: 100%;
    height: auto;
    margin-bottom: 1rem;
  }

  .scene-description p {
    text-align: center;
    margin: 0.5rem 0;
  }
</style>
