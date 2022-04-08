<template>
  <div class="background">
    <div class="block" :class="{clicked: clicked}" @click="closeBlock">
      <!-- <div  /> -->
    </div>
  </div>
</template>

<script>
export default ({
  // props: ["clicked"],
  data() {
    return {
      clicked: false,
    }
  },
  methods: {
    closeBlock() {
      this.clicked = true
      this.$emit("close")
    }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .background {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
  }
  .block {
    /* margin: 20px auto auto auto;
    width: 500px;
    height: 500px;
    background-color: aqua; */
    width: 720px;
    height: 500px;
    padding: 20px;
    margin: 100px auto;
    background: aqua;
    border-radius: 10px;
  }

  .clicked {
    background-color: #00ff00;
  }
</style>
