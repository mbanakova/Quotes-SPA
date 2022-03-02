<template>
	<div class="container">
		<div class="alert alert-info">{{ warningText }}</div>

		<Header :quotesCount="quotes.length" :maxQuotes="maxQuotes" />
		<new-quote @quoteAdded="newQuote"></new-quote>
		<quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></quote-grid>
	</div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid";
import NewQuote from "./components/NewQuote";
import Header from "./components/Header";

export default {
	components: {
		QuoteGrid,
		NewQuote,
		Header,
	},
	data() {
		return {
			quotes: [],
			maxQuotes: 10,
		};
	},
	computed: {
		warningText() {
			if (this.quotes.length > 0 && this.quotes.length < this.maxQuotes) {
				return "Click on a quote to delete it";
			} else if (this.quotes.length === this.maxQuotes) {
				return "You've added 10 quotes. Delete some before adding a new one";
			} else {
				return "Start typing!";
			}
		},
	},
	methods: {
		newQuote(quote) {
			if (this.quotes.length >= this.maxQuotes) {
				return;
			}
			this.quotes.push(quote);
		},
		deleteQuote(index) {
			this.quotes.splice(index, 1);
		},
	},
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.css";

#app {
	display: flex;
	flex-direction: column;
	align-items: center;
	min-height: 100vh;
}

.alert {
	margin-bottom: 50px;
	text-align: center;
}
</style>
