<template>
  <div class="results">
    reaction time is {{ this.score }} ms
    <br><br><br>
   <span>{{ this.rank }}</span>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: ["score"],

  data() {
    return {
      rank: null,
    };
  },

  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.score < 400) {
      this.rank = "Rapid flexes";
    } else {
      this.rank = "Snail.pace";
    }
  },

  methods: {},
};
</script>

<style scoped>
.results {
  width: 30vw;
  height: 4vh;
  border-radius: 10%;
  padding: 5%;
  margin-top: 1%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  position: relative;
  left: 50%;
  transform: translate(-50%);
  font-size: 2.5vh;
  font-weight: bolder;
}

.results > span {
    color: #0faf87;
}
</style>
