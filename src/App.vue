<template>
  <div id="app" class="container">
    <component :is="'quotes-grid-header'" :quoteLen="quoteLen" :maxLen="maxLen"></component>

    <component :is="'quotes-grid-new'" :quoteLen="quoteLen" @add-quote="addQuote"></component>

    <component :is="'quotes-grid'" :quotes="quotes" @rmv-quote="rmvQuote"></component>

    <component :is="'quotes-info'">{{ info[0] }}</component>

    <hr />

    <component :is="'quotes-counter'" :quoteLen="quoteLen" :maxLen="maxLen"></component>

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

    <component :is="'quotes-info'">{{ info[1] }}</component>
  </div>
</template>

<script>
import QuotesCounter from "./components/QuotesCounter.vue";
import QuotesNew from "./components/QuotesNew.vue";
import QuotesInfo from "./components/QuotesInfo.vue";
import QuotesCard from "./components/QuotesCard.vue";
import QuotesGridHeader from "./components/QuotesGridHeader.vue";
import QuotesGrid from "./components/QuotesGrid.vue";
import QuotesGridNew from "./components/QuotesGridNew.vue";

export default {
  components: {
    "quotes-counter": QuotesCounter,
    "quotes-new": QuotesNew,
    "quotes-info": QuotesInfo,
    "quotes-card": QuotesCard,
    "quotes-grid": QuotesGrid,
    "quotes-grid-new": QuotesGridNew,
    "quotes-grid-header": QuotesGridHeader
  },

  data() {
    return {
      maxLen: 10,
      quotes: [
        "They can't take that away from me",
        "Vivo sonhando mil horas sem fim",
        "Coisa mais bonita é você",
        "Heart to heart, lips to lips, we're chained and bound together",
        "In everyway you're mine",
        "The way you move your hair"
      ],
      info: [
        "Info: You can delete the quotes by clicking on them.",
        "Info: You can either copy the quote or delete it by clicking on the right top buttons."
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
      if (this.quoteLen < this.maxLen) {
        this.quotes.push(newQuote);
      } else {
        alert("You've added 10 quotes already");
      }
    },

    rmvQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style scoped>
#app {
  font-family: Arial, Helvetica, sans-serif;
}

.quotesList {
  overflow: auto;
  padding-bottom: 5px;
}
</style>
