<template>
  <h1>{{ title }}</h1>
  <!-- <button class="startBtn" :class="{clicked: waitingBlock}" @click="handleStartClick">{{ buttonText }}</button> -->
  <button 
    type="button" 
    class="btn btn-primary startBtn" 
    :class="{clicked: waitingBlock}"
    :disabled="waitingBlock"
    @click="handleStartClick"
  >
    Start
  </button>
  <ReactiveBlock @close="handleCloseBlock" v-if="showBlock" />
  <ResultDetail :reactionTime="reactionTime" v-if="showResult" />
</template>

<script>
import ReactiveBlock from './components/ReactiveBlock.vue'
import ResultDetail from './components/ResultDetail.vue'

export default {
  name: 'App',
  data() {
    return {
      title: "Reaction Time Test",
      buttonText: "Start",
      waitingBlock: false,
      showBlock: false,
      showResult: false,
      // startTime: null,
      // endTime: null,
      reactionTime: null,
    }
  },
  components: {
    ReactiveBlock,
    ResultDetail,
  },
  methods: {
    handleStartClick() {
      this.showResult = false
      this.buttonText = "waiting..."
      this.waitingBlock = true
      
      setTimeout(()=>{
        this.buttonText = "Click!"
        this.waitingBlock = false
        this.showBlock = true
        this.reactionTime = performance.now()
      }, 2000 + Math.random()*5000)
    },
    handleCloseBlock() {
      this.showBlock = false
      this.showResult = true
      this.reactionTime = performance.now() - this.reactionTime
      this.buttonText = "Start"
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.startBtn {
  width: 80px;
  text-align: center;
  margin-left: auto;
  margin-right: auto;
}

// .clicked {

// }
</style>
