<template lang="">
  <div class="block" @click="stopTimer" v-if="showBlock">click here 👌</div>
</template>
<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  updated() {
    console.log('updated to DOM')
  },
  unmounted() {
    console.log('unmounted from DOM')
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    },
  },
}
</script>
<style lang="css">
.block {
  width: 400px;
  border-radius: 20px;
  background-color: #0fa087;
  color: #fff;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  cursor: pointer;
}
</style>
