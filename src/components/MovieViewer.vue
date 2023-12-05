<template>
  <div class="movie-viewer-container">
    <!-- Close button -->
    <button class="close-button" @click="closeViewer">X</button>

    <!-- Movie title -->
    <h2>{{ movieTitle }}</h2>

    <!-- Loading indicator -->
    <div v-if="isLoading" class="loading-container">
      <img src="./assets/loading.gif" alt="Loading" class="loading-gif"/>
      <p class="loading-text">Loading clip {{ currentClipIndex + 1 }} of {{ movieSegments.length }}...</p>
    </div>

    <!-- Video container -->
    <div v-else class="video-container">
      <video ref="videoPlayer" :src="currentClipPath" class="video-player" controls @loadeddata="onClipLoaded"></video>
      <div class="navigation-buttons">
        <button v-if="currentClipIndex > 0" @click="previousClip" class="nav-button">Previous</button>
        <button @click="playMovie" class="play-button">Play</button>
        <button v-if="currentClipIndex < movieSegments.length - 1" @click="nextClip" class="nav-button">Next</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: {
    movieSegments: Array,
    movieTitle: String
  },
  data() {
    return {
      isLoading: false,
      currentClipIndex: 0,
      videoPlayer: null
    };
  },
  computed: {
    currentClipPath() {
      return `src/components/assets/${this.movieSegments[this.currentClipIndex]}_movie.mp4`;
    }
  },
  methods: {
    loadClip() {
      this.isLoading = true;
      // Simulate clip loading
      setTimeout(() => {
        this.isLoading = false;
        this.playMovie();
      }, 1000); // Adjust loading time as needed
    },
    playMovie() {
      if (!this.videoPlayer) {
        this.videoPlayer = this.$refs.videoPlayer;
      }
      this.videoPlayer.src = this.currentClipPath;
      this.videoPlayer.play();
    },
    onVideoEnded() {
      if (this.currentClipIndex < this.movieSegments.length - 1) {
        this.currentClipIndex++;
        this.loadClip(); // Load next clip
      }
    },
    nextClip() {
      if (this.currentClipIndex < this.movieSegments.length - 1) {
        this.currentClipIndex++;
        this.loadClip();
      }
    },
    previousClip() {
      if (this.currentClipIndex > 0) {
        this.currentClipIndex--;
        this.loadClip();
      }
    },
    onClipLoaded() {
      this.isLoading = false;
    },
    closeViewer() {
      this.$emit('close');
    }
  },
  mounted() {
    this.videoPlayer = this.$refs.videoPlayer;
    this.loadClip(); // Load first clip
  }
}
</script>

<style scoped>


h2 {
  margin-top: 0;
  text-align: center;
}

.video-player {
  width: 100%;
  max-height: 500px;
}
  .navigation-buttons {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
  }

  .nav-button {
    padding: 5px 10px;
    background-color: orange; /* Updated color for navigation buttons */
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    margin: 0 5px;
  }

  .play-button {
    padding: 5px 10px;
    background-color: #4CAF50; /* Green color for play button */
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
  }

  .movie-viewer-container {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    padding: 20px;
    padding-top: 40px; /* Increased padding-top to make space for the close button */
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    z-index: 1000;
    max-width: 80%;
    max-height: 80%;
    overflow: auto;
  }

  .close-button {
    position: absolute;
    top: 10px; /* Position at the top within the container */
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
  width: 50px;
}
  </style>

  