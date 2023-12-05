<template>
  <div class="scene-detail-container">
    <div class="scene-detail-header">
      <h2>{{ scene.segment }}</h2>
      <button class="close-button" @click="closeForm">X</button>
    </div>
    <div class="scene-content">
      <template v-if="isLoading">
        <div class="loading-indicator">Processing...</div>
      </template>
      <template v-else-if="videoLoaded">
        <video ref="videoPlayer" :src="videoUrl" class="scene-thumbnail" controls></video>
        <button class="close-button" @click="closeForm">Close</button>
      </template>
      <template v-else>
        <img :src="`./src/components/assets/${scene.segment}.png`" class="scene-thumbnail" alt="Movie Scene" />
        <div class="scene-description">
          <p>{{ scene.description }}</p>
          <p>Est. Processing time: {{ scene.estProcessingTime }}</p>
        </div>
        <button class="mint-button" @click="mintScene">Mint</button>
      </template>
    </div>
  </div>
</template>


<script>
import Replicate from "replicate";

export default {
  props: {
    scene: Object
  },
  data() {
    return {
      isLoading: false,
      videoUrl: null, // URL of the processed video
      videoLoaded: false // Indicates if the video is loaded
    };
  },
  methods: {
    closeForm() {
      this.$emit('close');
    },
    async mintScene() {
      this.isLoading = true;

      // Set up Replicate API call
      const replicate = new Replicate({
        auth: process.env.REPLIT_TOKEN,
      });

      try {
        const output = await replicate.run(
          "stability-ai/stable-video-diffusion:49fa7a9e0b5ffcf1b8172438",
          {
            input: {
              input_image: process.env.BASE_PATH + this.scene.segment
              // Add other parameters as required
            }
          }
        );

        // Mock delay for the processing time
        setTimeout(() => {
          this.isLoading = false;
          this.videoLoaded = true;
          this.videoUrl = `path/to/your/assets/${this.scene.segment}_movie.mp4`; // Set the movie clip URL
        }, 5000); // 5 seconds delay for loading
      } catch (error) {
        console.error("Error processing scene:", error);
        this.isLoading = false;
      }
    },
    viewVideo() {
      if (this.videoUrl) {
        // Open the video in a new tab or modal
        window.open(this.videoUrl, '_blank');
      }
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
    padding: 0.5rem 1rem; /* Adjust padding as needed */
    background-color: whitesmoke; /* Background color of the header */
    color: black; /* Color of the header title */
    display: flex;
    justify-content: space-between; /* Space out title and close button */
    align-items: center; /* Vertically center the items in the header */
    width: 100%; /* Header should span the full width of the container */
    box-sizing: border-box;
  }
  

  .scene-detail-header, .scene-content  {
    width: 70%;
  }

  .close-button {
    font-size: 1.5rem; /* Larger font size for the close button */
    cursor: pointer; /* Pointer on hover */
    margin-right: 1rem; /* Space from the right edge */
    background: none;
    border: none;
  }

  .close-button:hover {
    opacity: 0.7; /* Slight transparency on hover */
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

  .play-button {
    padding: 0.5rem 1rem;
    background-color: orange; /* Set the background color to orange */
    color: white;
    border: none;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
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

  .loading-indicator {
    display: flex;
    justify-content: center;
    align-items: center;
    /* add more styles as needed */
  }

  .play-button {
    /* Add your styling here */
  }
</style>
