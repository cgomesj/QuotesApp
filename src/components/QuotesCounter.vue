<template>
  <div class="QuotesCounter">
    <h1>Quotes Added</h1>
    <div class="quotes-counter-back">
      <div :style="{ width: quoteBarSize + '%'}" class="quoter-counter-bar" :class="quoteBarFull">
        <span class="quote-len">{{ quoteLen }} / 10</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuotesCounter",

  props: {
    quoteLen: Number,
    maxLen: Number
  },

  computed: {
    quoteBarSize() {
      return this.quoteLen * 10;
    },

    quoteBarFull() {
      return {
        "quote-bar-full": this.quoteLen == this.maxLen
      };
    }
  }
};
</script>

<style scoped>
.QuotesCounter {
  margin-top: 40px;
}

.quotes-counter-back {
  margin-top: 20px;
  width: 100%;
  height: 20px;
  background-color: #eee;
  border-radius: 5px;
}

.quoter-counter-bar {
  height: 100%;
  background-color: rgb(56, 131, 165);
  border-radius: 5px 0 0 5px;
  text-align: center;
}

.quote-len {
  color: white;
  font-weight: 700;
  height: 100%;
}

.quote-bar-full {
  border-radius: 5px;
}
</style>