<template>
  <div>
    <p class="scoreOutput">Reaction Time: {{ score }}ms</p>
    <p>{{ rank }}</p>
  </div>
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
    if (this.score < 250) {
      this.rank = "Blazing Fast";
    } else if (this.score < 400) {
      this.rank = "Fast Flexes";
    } else {
      this.rank = "Snail pace...";
    }
  },
};
</script>

<style>
.scoreOutput {
  font-weight: bold;
}
</style>