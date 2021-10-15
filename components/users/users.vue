<template>
	<article>
		<div v-for="(user, index) in results" :key="index">
			<User
				:user="user"
				class="item"
				:class="{ hightlight: selected === index }"
				@click.native="selected = index"
			/>
		</div>
	</article>
</template>

<script>
import User from './user'
import usersData from '~/assets/users.json'

export default {
	components: {
		User,
	},

	data() {
		return {
			searchKey: '',
			users: usersData,
			selected: null,
			results: usersData.slice(0, 20),
		}
	},

	created() {
		this.searchKey = this.$route.params.searchKey
		if (this.searchKey === undefined) {
			this.users = usersData
			this.results = usersData.slice(0, 20)
		} else {
			const query = this.searchKey.trim().toLowerCase()
			const newSearchResult = this.users.filter(
				(user) =>
					user.name.trim().toLowerCase().includes(query) ||
					user.title.trim().toLowerCase().includes(query) ||
					user.address.trim().toLowerCase().includes(query) ||
					user.city.trim().toLowerCase().includes(query) ||
					user.email.trim().toLowerCase().includes(query)
			)
			this.users = newSearchResult
			this.results = newSearchResult.slice(0, 20)
		}
	},
}
</script>

<style lang="scss" scoped>
.item {
	margin-top: 1rem;
	border-radius: 2px;
	background: #fafafa;
}
</style>
