<template>
  <div id="app">
    
    <component :is="'quotes-counter'" :quoteLen="quoteLen"></component>

    <component :is="'quotes-new'" :quoteLen="quoteLen" @add-quote="addQuote"></component>

    <div class="quotesList">
      <component
        :is="'quotes-card'"
        v-for="(quote, index) in quotes"
        :key="index"
        :quote="quote"
        :ind="index"
        @rmv-quote="rmvQuote"
      >
        <h3>{{ quote }}</h3>
      </component>
    </div>

    <component :is="'quotes-info'"></component>
  </div>
</template>

<script>
import QuotesCounter from "./components/QuotesCounter.vue";
import QuotesNew from "./components/QuotesNew.vue";
import QuotesInfo from "./components/QuotesInfo.vue";
import QuotesCard from "./components/QuotesCard.vue";

export default {
  components: {
    "quotes-counter": QuotesCounter,
    "quotes-new": QuotesNew,
    "quotes-info": QuotesInfo,
    "quotes-card": QuotesCard
  },

  data() {
    return {
      quotes: [
        "They can't take that away from me",
        "Vivo sonhando mil horas sem fim",
        "Coisa mais bonita é você",
        "Heart to heart, lips to lips, we're chained and bound together",
        "In everyway you're mine",
        "The way you move your hair"
      ]
    };
  },

  computed: {
    quoteLen() {
      return this.quotes.length;
    }
  },

  methods: {
    addQuote(newQuote) {
      this.quotes.push(newQuote);
    },

    rmvQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style scoped>
#app {
  width: 80%;
  margin: 0 auto;
  font-family: Arial, Helvetica, sans-serif;
}

.quotesList {
  overflow: auto;
  padding-bottom: 5px;
}
</style>
