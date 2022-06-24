<template>
  <div id="app">
    <h1>How fast can u catch me?</h1>
    <div class="fixed">
      <button class="btn" @click="start" :disabled="isPlaying">
        play game
      </button>
    </div>
  </div>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame" />
  </div>
  <div id="app" v-if="end">
    <Result :score="score" />
  </div>
</template>

<script>
import Block from "./components/BlockGame.vue";
import Result from "./components/ResultGame.vue";

export default {
  name: "App",
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      end: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 2500;
    },
    endGame(score) {
      this.score = score;
      this.isPlaying = false;
      this.end = true;
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #00287e;
  margin-top: 30px;
}
.fixed {
  width: 100%;
  height: 80px;
}
.btn {
  background-color: limegreen;
  color: white;
  padding: 15px 25px 15px 25px;
  border-radius: 15px;
  border: none;
  font-weight: bold;
  font-size: 16px;
  margin: 15px auto;
}
.btn[disabled] {
  background-color: rgb(104, 104, 104);
  color: rgb(0, 0, 0);
  padding: 15px 25px 15px 25px;
  border-radius: 15px;
  border: none;
  font-weight: bold;
  font-size: 16px;
  margin: 15px auto;
}
.btn:hover:enabled {
  background-color: rgb(32, 131, 223);
  color: white;
  padding: 15px 25px 15px 25px;
  border-radius: 15px;
  border: none;
  font-weight: bold;
  font-size: 15px;
  margin: 15px auto;
}
</style>
