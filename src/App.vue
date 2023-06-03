<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: "app",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false
    }
  },
  methods: {
    start() {
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.showScore = false
    },
    endTime(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showScore = true
    }
  } 
}
</script>

<template>
  <div class="rtContainer">
    <h1>Reaction timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endTime"/>
    <Results v-if="showScore" :score="score"/>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

.rtContainer {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

button {
  padding: 10px 16px;
  margin-top: 20px;
  background-color: darkslateblue;
  cursor: pointer;
  border: none;
  border-radius: 5px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
