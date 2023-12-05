<template>
  <div class="movie-viewer-container">
    <button class="close-button" @click="closeViewer">X</button>
    <h2>{{ movieTitle }}</h2>
    <div v-if="isLoading" class="loading-container">
      <img src="./src/components/assets/loading.gif" alt="Loading" class="loading-gif"/>
      <p class="loading-text">Please wait ...</p>
    </div>
    <div v-else class="video-container">
      <video ref="videoPlayer" :src="movieClipPath" class="video-player" controls></video>
      <button @click="playMovie" class="play-button">Play</button>
    </div>
  </div>
</template>


<script>
export default {
  props: {
    movieClipPath: String,
    movieTitle: String
  },
  data() {
    return {
      isLoading: true // Assume loading at the start
    };
  },
  mounted() {
    // Simulate a loading time
    setTimeout(() => {
      this.isLoading = false;
    }, 5000); // Adjust the time as needed
  },
  methods: {
    playMovie() {
      const videoPlayer = this.$refs.videoPlayer;
      if (videoPlayer.paused) {
        videoPlayer.play();
      } else {
        videoPlayer.pause();
      }
    },
    closeViewer() {
      this.$emit('close');
    }
  }
}
</script>



<style scoped>
.movie-viewer-container {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  z-index: 1000;
  max-width: 80%;
  max-height: 80%;
  overflow: auto;
}

h2 {
  margin-top: 0;
  text-align: center;
}

.video-player {
  width: 100%;
  max-height: 500px;
}

.play-button {
  margin-top: 10px;
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: transparent;
  border: none;
  font-size: 20px;
  cursor: pointer;
  color: black;
}

.loading-gif {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50px; /* Adjust as needed */
  height: 50px; /* Adjust as needed */
}

.loading-container, .video-container {
  display: none;
}

.loading-container {
  display: block;
}

  .loading-text {
    color: black; /* Ensuring the text is visible */
    text-align: center;
    margin-top: 10px;
  }

</style>

