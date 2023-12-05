<template>
  <div class="movie-grid-container">
    <div class="movie-grid">
      <MovieSquare
        v-for="(movie, index) in movies"
        :key="index"
        :imagePath="getImagePath(movie.segment)" 
        :isMint="movie.isMint"
        @squareClicked="openSceneDetail(movie)"
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
          { isMint: true, segment: 'scene_1', description: "The beginning of the movie, the ninja discovers a hidden castle in the mountains." },
          { isMint: false, segment: 'scene_2', description: "After being captured by her guards, the ninja is brought before the queen of the realm." },
          { isMint: true, segment: 'scene_3', description: "Outraged by his tresspassing, the queen commands the ninja to battle an ancient creature from beneath the castle who has been plauging the kingdom for years."  },
          { isMint: false, segment: 'scene_4' , description: "After defeating the monster, the hero is crowned with the highest honor of the realm."  },
          { isMint: true, segment: 'scene_5', description: "The ninja is married to the queen of the kingdom as foretold by an ancient prophecy."  },
          { isMint: false, segment: 'scene_6' , description: "Jealous rivals dispatch assassins to attempt to slay the hero."  },
          { isMint: true, segment: 'scene_7' , description: "A dragon is released by the witch king of a nearby kingdom after his attempts at assassination fail."  },
          { isMint: false, segment: 'scene_8' , description: "After slaying the dragon, the ninja finds a nest of eggs with a single surviving infant dragon, which he takes back to the queen."  }
        ],
        isSceneDetailVisible: false,
        selectedScene: null,
      };
    },
    methods: {
      openSceneDetail(movie) {
        this.selectedScene = { movie, imagePath: this.getImagePath(movie.segment) };
        this.isSceneDetailVisible = true;
      },
      getImagePath(segment) {
        return `src/components/assets/${segment}.png`;
      },
    },
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
    height:100%;
    width:100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: transparent; /* Semi-transparent background */
  }
</style>
