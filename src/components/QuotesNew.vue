<template>
  <div class="QuotesNew">
    <h5>New Quote</h5>
    <textarea
      @keyup.enter="addQuote"
      v-model="tempText"
      placeholder="Press 'Enter' key or click the button bellow to add new quote."
    ></textarea>
    <button @click="addQuote">Add Quote</button>
  </div>
</template>

<script>
export default {
  name: "QuotesNew",

  props: {
    quoteLen: Number
  },

  data() {
    return {
      tempText: ""
    };
  },

  methods: {
    addQuote() {
      if (this.quoteLen < 10) {
        this.$emit("add-quote", this.tempText);
        this.tempText = "";
      } else {
        alert("You've added 10 quotes already");
      }
    }
  }
};
</script>

<style scoped>
.QuotesNew {
  width: 50%;
  margin: 40px auto;
}

.QuotesNew > h5 {
  font-weight: 700;
}

.QuotesNew > textarea {
  width: 100%;
  height: 100px;
  padding: 10px;
  resize: none;
}

.QuotesNew > button {
  width: 30%;
  height: 40px;
  margin-top: 5px;
}
</style>