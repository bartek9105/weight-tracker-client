<template>
	<button class="btn">
		<slot></slot>
	</button>
</template>

<script>
export default {
	name: 'Button'
}
</script>

<style lang="scss" scoped>
.btn {
	font-weight: 500;
	border: 2px solid #fff;
	border-radius: 5px;
	padding: 0.5rem 2rem;
	color: #fff;
	background: none;
	cursor: pointer;
	&:hover {
		box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
		transition: 0.2s ease-in-out;
	}
}
</style>
