<template>
  <p class="time">Reaction Time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>
<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 150) {
      this.rank = "Wow! FAST!";
    } else if (this.score < 250) {
      this.rank = "Good Job";
    } else if (this.score < 400) {
      this.rank = "Not Bad";
    } else {
      this.rank = "Hmmm, you can be better";
    }
  },
};
</script>
<style scoped>
.time {
  font-size: 1.25rem;
  margin-bottom: 0.75rem;
}
.rank {
  color: #0faf87;
  font-weight: bold;
}
</style>
