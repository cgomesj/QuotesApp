<template>
  <div class="row">
    <component
      :is="'quotes-grid-item'"
      v-for="(quote, index) in quotes"
      :key="index"
      @click.native="rmvQuote(index)"
    >{{ quote }}</component>
  </div>
</template>

<script>
import QuotesGridItem from "./QuotesGridItem.vue";

export default {
  components: {
    "quotes-grid-item": QuotesGridItem
  },

  props: {
    quotes: Array
  },

  methods: {
    rmvQuote(index) {
      this.$emit("rmv-quote", index);
    }
  }
};
</script>

<style scoped>
</style>