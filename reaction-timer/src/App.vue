<template>
  <h1>Ninja Reaction Timer</h1>
  <button class="btn" @click="startGame" :disabled="isPlaying" :class="{ disabled: isPlaying }">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showReaction" :reactionTime="reactionTime"/>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      showReaction: false,
      delay: null,
      reactionTime: null
    }
  },
  methods: {
    startGame() {
      this.isPlaying = true
      this.showReaction = false
      this.delay = 2000 + (Math.random() * 5000)
    },
    endGame(reactionTimer) {
      this.isPlaying = false
      this.showReaction = true
      this.reactionTime = reactionTimer
    }
  },
  components: { Block, Results }
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

.btn {
  padding: 15px 10px;
  background-color: #222;
  border: transparent;
  border-radius: 10px;
  font-weight: bold;
  color: #181;
}

.disabled {
  background-color: #555;
  cursor: not-allowed;
}
</style>
