<template>
  <form class="my-5">
    <div class="form-group mx-auto col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
      <label for="addQuote">New Quote</label>
      <textarea id="addQuote" class="form-control" rows="3" v-model="quote" @keyup.enter="addQuote"></textarea>
    </div>
    <div class="mx-auto col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
      <button @click.prevent="addQuote" class="btn btn-primary">Add Quote</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "QuotesGridNew",

  props: {
    quoteLen: Number
  },

  data() {
    return {
      quote: ""
    };
  },

  methods: {
    addQuote() {
      this.$emit("add-quote", this.quote);
      this.quote = "";
    }
  }
};
</script>

<style scoped>
</style>