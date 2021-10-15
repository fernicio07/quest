<template>
	<div class="users-page">
		<SearchBar />
		<Users />
	</div>
</template>

<script>
import SearchBar from '~/components/shared/SearchBar'
import Users from '~/components/users/users'

export default {
	components: {
		SearchBar,
		Users,
	},
}
</script>

<style lang="scss">
.users-page {
	background-color: #fff;
	padding: 1rem;
}
</style>
