<template>
	<div class="search-bar">
		<v-icon class="icon" color="#7f7f7f"> mdi-magnify </v-icon>
		<input
			v-model="query"
			type="text"
			class="fa form-control__input"
			placeholder="Search by name, title or email and press enter"
			@keydown.enter="handleChange"
		/>
	</div>
</template>

<script>
export default {
	data() {
		return {
			query: '',
		}
	},
	methods: {
		handleChange() {
			this.$router.push(`/search/${this.query}`)
		},
	},
}
</script>

<style lang="scss" scoped>
.search-bar {
	background-color: #f5f5f5;
	display: flex;
	padding-left: 1rem;
	width: 100%;

	.icon {
		font-size: 1.4rem;
	}

	input {
		background-color: #f5f5f5;
		font-size: 1.4rem;
		height: 3rem;
		padding-left: 0.5rem;
		width: 95%;

		:focus-visible {
			outline: none;
		}
	}
}
</style>
