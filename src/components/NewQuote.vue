<template>
	<div class="row">
		<form>
			<label for="textarea">Quote</label>
			<textarea
				v-model="quote"
				rows="3"
				:ref="'textarea'"
				id="textarea"
			></textarea>
			<button class="button" @click.prevent="createNew">Add quote</button>
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			quote: "",
		};
	},
	methods: {
		createNew() {
			if (this.quote === "") {
				return;
			}
			this.$emit("quoteAdded", this.quote);
			this.quote = "";
			this.$refs["textarea"].focus();
		},
	},
};
</script>

<style scoped>
form {
	display: flex;
	flex-direction: column;
	align-items: center;
}

label {
	font-size: 26px;
	font-weight: 500;
	margin-bottom: 5px;
}
textarea {
	resize: vertical;
	max-width: 600px;
	width: 100%;
	margin-bottom: 20px;
	padding: 10px 20px;
	border: 2px solid #a2a1a1;
}
textarea:focus {
	background-color: rgb(246, 251, 255);
	outline: none;
	border: 2px solid #54c1da;
}
.button {
	background-color: #e32636;
	border: none;
	cursor: pointer;
	color: white;
	padding: 10px 30px;
	border-radius: 6px;
	margin-bottom: 40px;
}
</style>
