<template>
  <div class="popup-container">
    <div class="popup-header">
      <h2>{{ title }}</h2>
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
  margin-bottom: 1rem;
}

.close-button {
  border: none;
  background: none;
  cursor: pointer;
  font-size: 1rem;
}

.popup-content p {
  color: black;
  text-align: left;
}
</style>
