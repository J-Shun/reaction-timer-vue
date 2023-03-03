<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click ME!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 300px;
  border-radius: 20px;
  background-color: #0faf87;
  color: #fff;
  font-size: 1.5rem;
  text-align: center;
  padding: 50px 0;
  margin: 40px auto;
  cursor: pointer;
}

.block:hover {
  background-color: #28b894;
}
</style>
