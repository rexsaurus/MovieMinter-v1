<template>
  <div
    :class="['movie-square', { 'mint': isMint }]"
    @mouseover="isMint && highlight()"
    @mouseleave="isMint && unhighlight()"
    @click="playMovieSegment"
  >
    <!-- Image or video content goes here -->
    <img :src="imagePath" class="scene-thumbnail" alt="Movie Scene" />
    
    <!-- Conditionally render "MINT" text for isMint = false -->
    <div v-if="!isMint" class="mint-text">MINT</div>
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
    border: 1px solid transparent; /* Default border set to transparent */
    cursor: pointer; /* Changes the cursor to a pointer on hover */
    transition: border-color 0.3s ease; /* Smooth transition for border color */

    /* Default background image and opacity */
    background-image: url('./assets/film_icon.png');
    background-size: 50%;
    background-repeat: no-repeat;
    background-position: center;
    opacity: 1; /* Default opacity for scenes with isMint = false */
    text-align: center; /* Center text horizontally */
    display: flex;
    align-items: center; /* Center text vertically */
    justify-content: center;
  }

/* Add styling for the scene-thumbnail image */
.scene-thumbnail {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Maintain aspect ratio and cover the entire container */
}

/* Apply 30% opacity to scenes with isMint = true */
.mint {
  opacity: 0.3;
}

/* Style for the "MINT" text */
.mint-text {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem; /* Adjust font size as needed */
  color: #ffffff; /* Text color */
  background-color: rgba(0, 0, 0, 0.3); /* Background color with 30% opacity */
}

/* Add green border on hover */
.movie-square:hover {
  border: 2px solid #42b983; /* Green border on hover */
}
</style>
