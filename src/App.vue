<template>
  <h1>Reaction Timer</h1>
  <button class="play-btn" @click="start" :disabled="isPlaying">Play</button>
  <Block :delay="delay" v-if="isPlaying" @end="endGame"> </Block>
  <Results v-if="this.score != null" :score="this.score"> </Results>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.score= null;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

.play-btn {
  font-size: 2vh;
  padding: 1vh;
  margin: 1vh, 1vw;
}
</style>
