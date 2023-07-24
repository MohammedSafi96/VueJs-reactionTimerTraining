<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Results v-if="showResults" :score="score"></Results>
  <div v-if="showModal">
    <Modal :exp1="exp1" @close="toggleModal">
      <h1>Hiii h1</h1>
      <p>this is MS</p>
      <template v-slot:links><a href="#">link 1</a></template>
    </Modal>
  </div>
  <button @click="toggleModal">open modal</button>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
import Modal from './components/Modal.vue'
export default {
  name: 'App',
  components: { Block, Results, Modal },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      exp1: 'Hi Modal',
      showModal: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + (Math.random() * 5000)
      this.isPlaying = true
      this.showResults = false
      console.log(`delay No: ${this.delay}`)
    },
    endGame(reactionTimer) {
      this.score = reactionTimer
      this.isPlaying = false
      this.showResults = true
    },
    toggleModal() {
      this.showModal = !this.showModal
    }
  }
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
