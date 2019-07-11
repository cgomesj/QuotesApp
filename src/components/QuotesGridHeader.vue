<template>
  <div class="row">
    <div class="col-sm-12">
      <h3>Quotes Added</h3>
      <div class="progress">
        <div
          class="progress-bar"
          :style="progressQuote"
          role="progressbar"
          aria-valuenow="60"
          aria-valuemin="0"
          aria-valuemax="100"
        >{{ quoteLen }} / {{ maxLen }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    quoteLen: Number,
    maxLen: Number
  },

  computed: {
    progressQuote() {
      return { width: (this.quoteLen / this.maxLen) * 100 + "%" };
    }
  }
};
</script>

<style scoped>
</style>