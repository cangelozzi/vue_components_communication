<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded='newQuote'></app-new-quote>
    <app-quote-grid :quotes='quotes' @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a quote to delete it.</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import newQuote from "./components/newQuote.vue";
import Header from "./components/Header.vue";
export default {
  data() {
    return {
      quotes: ["My first Quote here"],
      maxQuotes: 10
    }
  },

  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: newQuote,
    appHeader: Header
  },

  methods: {
    newQuote(quote) {
      if(this.quotes.length >= this.maxQuotes) {return alert("Please DELETE a quote first, before entering the next!")}
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }

};
</script>

<style>
</style>
