<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      buttonContent: "Play",
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.buttonContent = "Wait";
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.buttonContent = "Play";
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<template>
  <div class="wrap">
    <h1>Reaction Timer</h1>
    <button class="start-btn" @click="start" :disabled="isPlaying">
      {{ buttonContent }}
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :score="score" />
  </div>
</template>

<style scoped>
.wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 7.5rem;
}

h1 {
  font-size: 3.5rem;
  margin-bottom: 4rem;
}

.start-btn {
  background-color: #0faf87;
  padding: 0.5rem 0;
  width: 8rem;
  font-size: 1.25rem;
  border: none;
  border-radius: 1.5rem;
  color: #fff;
  margin-bottom: 2rem;
  cursor: pointer;
}

.start-btn:hover {
  background-color: #28b894;
}

.start-btn:disabled {
  background-color: #ccc;
  cursor: default;
}
</style>
