<template>
  <h1>Reaction timer</h1>
  <button @click="start" :disabled="isPlaying">Play 😍</button>
  <TheBlock v-if="isPlaying" :delay="delay" @end="endGame" />
  <TheResults v-if="showResult" :time="time" />
</template>

<script>
import TheBlock from './components/TheBlock.vue'
import TheResults from './components/TheResults.vue'

export default {
  name: 'App',
  components: { TheBlock, TheResults },
  data() {
    return {
      delay: null,
      isPlaying: false,
      time: null,
      showResult: false,
    }
  },
  methods: {
    start() {
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 1000
      this.showResult = false
    },
    endGame(reactionTime) {
      this.isPlaying = false
      this.time = reactionTime
      this.showResult = true
    },
  },
}
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
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
