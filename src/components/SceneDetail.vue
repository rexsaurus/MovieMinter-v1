<template>
  <div class="scene-detail-container">
    <div class="scene-detail-header">
      <h2>{{ scene.segment }}</h2>
      <button class="close-button" @click="closeForm">X</button>
    </div>
    <div class="scene-content">
      <img :src="scene.imagePath" class="scene-thumbnail" alt="Movie Scene" />
      <div class="scene-description">
        <p>In this scene, the character</p>
        <p>{{ scene.description }}</p>
        <p>Est. Processing time: {{ scene.estProcessingTime }}</p>
      </div>
      <button class="mint-button" @click="closeForm">Mint</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    scene: Object
  },
  methods: {
    closeForm() {
      this.$emit('close');
    }
  }
};
</script>

<style scoped>
.scene-detail-container {
  background-color: transparent; /* Adjust the alpha value for 70% opacity */
  padding: 15% 15% 2rem; /* 15% on the sides and 2rem at the bottom */
  box-sizing: border-box; /* Ensures padding is included in width calculation */
  position: fixed; /* Full-screen overlay */
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 1000; /* High z-index to overlay on top of other content */
}

.scene-detail-header {
  padding: 0.5rem 1rem;
  background-color: whitesmoke;
  color: black; /* Set header text color to black */
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-sizing: border-box;
}

  .scene-detail-header, .scene-content  {
    width: 70%;
  }

.close-button {
  border: none;
  background: none;
  cursor: pointer;
  font-size: 1.5rem;
}

.scene-content {
  display: flex;
  flex-direction: column;
  align-items: center;
 /* Adjust to control the size of the content area */
  background-color: whitesmoke; /* Ensure content area has a solid white background */
  padding: 1rem;
  box-sizing: border-box;
}

.scene-thumbnail {
  width: 100%;
  height: auto;
  margin-bottom: 1rem;
}

.scene-description p {
  color: black; /* Set description text color to black */
  text-align: center;
  margin: 0.5rem 0;
}

.mint-button {
  padding: 0.5rem 1rem;
  margin-top: 1rem; /* Space from the text above */
  margin-bottom: 2rem; /* Space from the bottom of the container */
  cursor: pointer;
  background-color: orange;
  color: white;
  border: none;
  border-radius: 5px;
  font-weight: bold;
  width: auto;
  font-size: 1.25rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2); /* Optional: add a shadow for depth */
}
</style>
