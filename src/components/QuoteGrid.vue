<template>
	<transition-group tag="ul" name="quotes-list" class="grid">
		<app-quote
			v-for="(quote, index) in quotes"
			:key="index"
			@click="deleteQuote(index)"
			>{{ quote }}</app-quote
		>
	</transition-group>
</template>

<script>
import Quote from "./Quote.vue";
export default {
	props: ["quotes"],
	components: {
		appQuote: Quote,
	},
	methods: {
		deleteQuote(index) {
			this.$emit("quoteDeleted", index);
		},
	},
};
</script>

<style>
.grid {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	gap: 20px;
	padding: 0;
	list-style: none;
	margin: 0 0 40px;
}

.quotes-list-enter-from {
	opacity: 0;
	transform: translateX(-30px);
}

.quotes-list-enter-active {
	transition: all 1s ease-out;
}

.quotes-list-leave-active {
	transition: all 1s ease-in;
	position: absolute;
}

.quotes-list-enter-to,
.quotes-list-leave-from {
	opacity: 1;
	transform: translateX(0);
}

.quotes-list-leave-to {
	opacity: 0;
	transform: translateX(30px);
}

.quotes-list-move {
	transition: transform 0.8s ease;
}
</style>
