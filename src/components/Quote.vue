<template>
	<li class="quote">
		<slot></slot>
	</li>
</template>

<script>
export default {};
</script>

<style>
.panel-body {
	font-family: "Arizonia", cursive;
	font-size: 24px;
	color: #6e6e6e;
}

.quote {
	cursor: pointer;
	padding: 30px;
	border-radius: 6px;
	background-color: #e2f0ff;
	font-size: 18px;
	text-align: center;
	margin: 0;
	list-style: none;
}

.quote:hover {
	background-color: #ffe2e2;
}
</style>
