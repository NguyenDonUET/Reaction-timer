<template lang="">
  <div class="result">Reaction time: {{ time }} ms</div>
  <p class="rank">{{ rank }}</p>
</template>
<script>
export default {
  props: ['time'],
  data() {
    return {
      rank: null,
    }
  },
  mounted() {
    if (this.time < 300) {
      this.rank = 'Ninja fingers 🐱‍👤'
    } else if (this.time < 500) {
      this.rank = 'Rapid reflexes 🐇'
    } else {
      this.rank = 'Con rùa (turtle)🐢'
    }
  },
}
</script>
<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
.result {
  margin-top: 10px;
}
</style>
