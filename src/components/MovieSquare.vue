<template>
  <div
    :class="['movie-square', { 'mint': isMint }]"
    @mouseover="isMint && highlight()"
    @mouseleave="isMint && unhighlight()"
    @click="playMovieSegment"
  >
    <!-- Image or video content goes here -->
    <img :src="imagePath" class="scene-thumbnail" alt="Movie Scene" />
  </div>
</template>

<script>
export default {
  props: {
    imagePath: String, // Add a prop to accept the image path
    isMint: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    highlight() {
      // Logic to highlight the square
    },
    unhighlight() {
      // Logic to unhighlight the square
    },
    playMovieSegment() {
      if (!this.isMint) {
        // Logic to play movie segment
      }
    }
  }
}
</script>

<style scoped>
.movie-square {
    background-color: #f0f0f0; /* Example background color */
    position: relative;
    width: 100%;
    height: 85px; /* Fixed height */

    /* Remove background-image and background-size properties */
    /* background-image: url('./assets/film_icon.png'); */
    /* background-size: 50%; */

    border: 1px solid transparent; /* Default border set to transparent */
    cursor: pointer; /* Changes the cursor to a pointer on hover */
    transition: border-color 0.3s ease; /* Smooth transition for border color */
}

/* Add styling for the scene-thumbnail image */
.scene-thumbnail {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Maintain aspect ratio and cover the entire container */
}

.movie-square:hover {
    color: #42b983; /* Changes text color on hover */
    border-color: #42b983; /* Changes border color on hover */
    border-width: 3px; /* Sets border width on hover */
    border-style: solid; /* Ensures the border style is solid */
}
</style>
