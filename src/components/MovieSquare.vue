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
  }

.movie-square.mint:hover {
  /* styles for hovering over mint squares */
}
</style>
