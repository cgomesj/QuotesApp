<template>
  <div class="QuotesCard">
    <small>#{{ ind + 1 }}</small>
    <button @click="rmvQuote" class="btnQuote btnDel">x</button>
    <button @click="copyQuote" class="btnQuote btnCopy">Copy</button>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "QuotesCard",

  props: {
    ind: Number,
    quote: String
  },

  methods: {
    rmvQuote() {
      this.$emit("rmv-quote", this.ind);
    },

    copyToClipboard(str) {
      const el = document.createElement("textarea");
      el.value = str;
      document.body.appendChild(el);
      el.select();
      document.execCommand("copy");
      document.body.removeChild(el);
    },

    copyQuote() {
      this.copyToClipboard(this.quote);
    }
  }
};
</script>

<style scoped>
.QuotesCard {
  width: 30%;
  min-height: 130px;
  background-color: #fefefe;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 1px 2px 3px #ccc;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  font-style: italic;
  padding: 1%;
  margin-top: 20px;
  margin-left: 10px;
  float: left;
  cursor: pointer;
}

.QuotesCard > small {
  color: #ccc;
}

.QuotesCard:hover {
  background-color: #fcfcfc;
}

.btnQuote {
  float: right;
  font-family: Arial, Helvetica, sans-serif;
  font-style: normal;
  margin-right: 5px;
}

.btnCopy {
  color: rgb(141, 141, 141);
}

.btnDel {
  color: rgb(255, 144, 144);
}
</style>