<template>
  <h1>Vue.js Reaction Game</h1>
  <button @click="startedGame" :disabled="isPlayed">Start game</button>
  <Block :delay="delay" v-if="isPlayed" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: "App",
  data() {
    return {
      isPlayed: false,
      delay: null,
      score: null,
      showResult: false
    };
  },
  components: {
    Block,
    Result
  },
  methods: {
    startedGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlayed = true;
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlayed = false
      this.showResult = true
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
