<template>
  <div class="movie-grid-container">
    <div class="movie-grid">
      <MovieSquare
        v-for="(movie, index) in movies"
        :key="index"
        :isMint="movie.isMint"
        :movieSegment="movie.segment"
        @click="openSceneDetail(movie)"
      />
    </div>
    <div class="scene-detail-popup" v-if="isSceneDetailVisible">
      <SceneDetail
        :scene="selectedScene"
        @close="isSceneDetailVisible = false"
      />
    </div>
  </div>
</template>

<script>
import MovieSquare from './MovieSquare.vue';
import SceneDetail from './SceneDetail.vue';

export default {
  components: {
    MovieSquare,
    SceneDetail
  },
  data() {
    return {
      movies: [
        { isMint: true, segment: 'scene_1' },
        { isMint: false, segment: 'scene_2' },
        { isMint: true, segment: 'scene_3' },
        { isMint: false, segment: 'scene_4' },
        { isMint: true, segment: 'scene_5' },
        { isMint: false, segment: 'scene_6' }
        // ...more movie objects
      ],
      isSceneDetailVisible: false,
      selectedScene: null,
    };
  },
  methods: {
    openSceneDetail(movie) {
      this.selectedScene = movie;
      this.isSceneDetailVisible = true;
    }
  }
};
</script>

<style scoped>
  .movie-grid-container {
    position: relative; /* This makes it a context for absolutely positioned children */
  }

  .movie-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 15px;
    padding: 15px;
    width: 100%;
  }

  .scene-detail-popup {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.5); /* Semi-transparent background */
  }
</style>
