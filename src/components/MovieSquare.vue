<template>
  <div
    :class="['movie-square', { 'mint': isMint }]"
    @mouseover="isMint && highlight()"
    @mouseleave="isMint && unhighlight()"
    @click="playMovieSegment"
  >
    <!-- Image or video content goes here -->
  </div>
</template>

<script>
export default {
  props: {
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
    padding-top: 25%; /* Height as a percentage of width */
    position: relative;
    width: 100%;
    height: 85px; /* Fixed height */

    background-image: url('./assets/film_icon.png'); /* Replace with the actual path to your icon */
    background-size: 50%; /* Adjust this value to scale the size of the image */
    background-repeat: no-repeat; /* Prevents the image from tiling */
    background-position: center; /* Centers the background image in the square */
 border: 1px solid transparent; /* Default border set to transparent */
  cursor: pointer; /* Changes the cursor to a pointer on hover */
  transition: border-color 0.3s ease; /* Smooth transition for border color */
}

  .movie-square:hover {
    color: #42b983; /* Changes text color on hover */
    border-color: #42b983; /* Changes border color on hover */
    border-width: 3px; /* Sets border width on hover */
    border-style: solid; /* Ensures the border style is solid */
  }
</style>
