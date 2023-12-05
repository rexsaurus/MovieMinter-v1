<template>
  <div class="popup-container">
    <div class="popup-header">
      <h2 class="popup-title">{{ title }}</h2>
      <button class="close-button" @click="closePopup">X</button>
    </div>
    <div class="popup-content">
      <p>{{ text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String, // Title for the popup
    text: String // Text content for the popup
  },
  methods: {
    closePopup() {
      this.$emit('close');
    }
  }
};
</script>
<style scoped>
.popup-container {
  background-color: rgba(255, 255, 255, 0.9); /* Semi-transparent white */
  padding: 2rem;
  box-sizing: border-box;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1000;
  width: 50%; /* Adjust as needed */
  border: 1px solid #ccc; /* Optional border */
  border-radius: 8px; /* Rounded corners */
}

  .popup-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%; /* Ensure the header spans the full width */
    margin-bottom: 1rem; /* Space between header and content */
  }

  .popup-title {
    font-size: 1.5rem; /* Larger font size for the title */
    font-weight: bold; /* Bold font weight for the title */
    margin-left: 1rem; /* Space from the left edge */
    color: black;
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

  .popup-content p {
    font-size: 1rem; /* Larger font size for content */
    font-weight: bold; /* Bold font weight for content */
    color: black; /* Text color */
    text-align: justify; /* Justify text alignment */
    margin: 0 1rem; /* Horizontal padding for the content */
  }
</style>
