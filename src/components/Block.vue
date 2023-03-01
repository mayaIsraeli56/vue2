<template>
  <div v-if="blockShowing" class="block" @click="stopTimer">{{ text }}</div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],

  data() {
    return {
      text: "click me fast!",
      blockShowing: false,
      timer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.blockShowing = true
      this.startTimer()
    }, this.delay)
  },

  methods: {
    startTimer() {
        this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10)
    },
    stopTimer() {
        clearInterval(this.timer)
        this.$emit("end",this.reactionTime )
        console.log(`the final reaction time is ${this.reactionTime}`)
    }
  },
};
</script>

<style scoped>
.block {
  width: 15vw;
  height: 6vh;
  border-radius: 10%;
  background-color: #0faf87;
  color: white;
  padding: 5%;
  margin-top: 5%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  position: relative;
  left: 50%;
  transform: translate(-50%);
}
</style>
