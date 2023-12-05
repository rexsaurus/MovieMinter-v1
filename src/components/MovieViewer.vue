<template>
  <div class="movie-viewer-container">
    <h2>{{ movieTitle }}</h2>
    <video ref="videoPlayer" :src="movieClipPath" class="video-player" controls></video>
    <button @click="playMovie" class="play-button">Play</button>
    <button @click="closeViewer" class="close-button">Close</button>
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
      // any additional data properties
    };
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

.play-button, .close-button {
  margin-top: 10px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.play-button {
  background-color: #4CAF50;
  color: white;
}

.close-button {
  background-color: #f44336;
  color: white;
}
</style>
