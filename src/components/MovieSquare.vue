<template>
  <div
    :class="['movie-square', { 'mint': isMint }]"
    @mouseover="isMint && highlight()"
    @mouseleave="isMint && unhighlight()"
    @click="$emit('squareClicked')"
  >
    <!-- Image or video content goes here -->
    <img :src="imagePath" class="scene-thumbnail" alt="Movie Scene" />
    <!-- Conditional rendering based on isMint -->
    <div v-if="!isMint" class="mint-text">MINT</div>
    <div v-if="isMint" class="unavailable-text">unavailable</div>
  </div>
</template>

<script>
export default {
  props: {
    segment: String, // Receive the segment name instead of the full image path
    isMint: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    // Compute the image path by appending '_small' to the segment
    imagePath() {
      return `./src/components/assets/${this.segment}_small.png`; // Adjust the path as needed
    }
  },
  methods: {
    highlight() {
      // Logic to highlight the square
      // Add your highlight logic here
    },
    unhighlight() {
      // Logic to unhighlight the square
      // Add your unhighlight logic here
    },
    playMovieSegment() {
      if (!this.isMint) {
        // Logic to play movie segment
        // Add logic to play the movie segment
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
      height: 120px; /* Fixed height */
      border: 1px solid transparent; /* Default border set to transparent */
      cursor: pointer; /* Changes the cursor to a pointer on hover */
      transition: border-color 0.3s ease; /* Smooth transition for border color */
      display: flex;
      align-items: center; /* Center text vertically */
      justify-content: center;
      text-align: center; /* Center text horizontally */
  }

  .scene-thumbnail {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Maintain aspect ratio and cover the entire container */
  }

  .mint {
    opacity: 0.3;
  }

  .mint-text, .unavailable-text {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px; /* Padding to avoid text touching the edges */
    word-wrap: break-word; /* Ensures long words do not overflow */
    overflow-wrap: break-word; /* Alternative to word-wrap */
    font-size: 2.5vw; /* Starting font size based on viewport width */
    color: #ffffff; /* Text color */
    text-shadow: 0 0 4px rgba(0,0,0,0.6); /* Text shadow for better readability */
  }

  .mint-text {
    background-color: rgba(0, 0, 0, 0.3); /* Background color with 30% opacity */
  }

  .unavailable-text {
    background-color: rgba(255, 0, 0, 0.3); /* Red background color with 30% opacity */
  }

  /* Media Queries for specific screen sizes */
  @media (max-width: 600px) {
    .mint-text, .unavailable-text {
      font-size: 4vw; /* Larger font size for smaller screens */
    }
  }

  @media (min-width: 601px) {
    .mint-text, .unavailable-text {
      font-size: 2.5vw; /* Adjust font size for medium screens */
    }
  }

  @media (min-width: 1024px) {
    .mint-text, .unavailable-text {
      font-size: 1.25vw; /* Smaller font size for larger screens */
    }
  }

</style>
