<template>
  <div class="movie-grid">
    <MovieSquare
      v-for="(movie, index) in movies"
      :key="index"
      :isMint="movie.isMint"
      :movieSegment="movie.segment"
    />
  </div>
</template>

<script>
import MovieSquare from './MovieSquare.vue';

export default {
  components: {
    MovieSquare
  },
  data() {
    return {
      // Example data structure for movies, you would fetch or calculate this data as required
      movies: [
        { isMint: true, segment: 'segment1.mp4' },
        { isMint: false, segment: 'segment2.mp4' },
        // ...more movie objects
      ]
    };
  }
};
</script>

<style scoped>
.movie-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 1rem;
  padding: 1rem;
  justify-items: center;
}
</style>
