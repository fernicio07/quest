<template>
	<article>
		<div class="card">
			<div class="card-img">
				<img class="card-img-top" :src="user.avatar" :alt="user.name" />
			</div>
			<div class="card-body">
				<div class="card-data">
					<div class="card-name" v-html="highlight(user.name)"></div>
					<div class="card-email" v-html="highlight(user.email)"></div>
				</div>
				<div class="card-title" v-html="highlight(user.title)"></div>
				<div
					class="card-address"
					v-html="highlight(`${user.city}, ${user.address}`)"
				></div>
				<v-divider></v-divider>
				<div class="card-link">
					<button>Mark as suitable</button>
				</div>
			</div>
		</div>
	</article>
</template>

<script>
export default {
	name: 'User',
	props: {
		user: Object,
	},
	data() {
		return {
			searchKey: '',
		}
	},
	created() {
		this.searchKey = this.$route.params.searchKey ?? ''
	},
	methods: {
		highlight(content) {
			if (!this.searchKey) {
				return content
			}
			return content.replace(new RegExp(this.searchKey, 'gi'), (match) => {
				return '<span style="background: yellow">' + match + '</span>'
			})
		},

		// TODO => Wait for req to add method for button
	},
}
</script>

<style lang="scss" scoped>
.card {
	color: #000;
	display: flex;

	.card-img {
		background: #bbbbbb;

		img {
			display: block;
			margin: 0 auto;
			height: 100%;
			width: 100%;
		}
	}

	.card-body {
		width: 100%;
		padding: 1rem 2rem;

		.card-data {
			display: flex;
			flex-direction: row;
			justify-content: space-between;

			.card-name {
				font-size: 1.4rem;
				line-height: 1.5;
			}
		}

		.card-title {
			font-size: 1rem;
			line-height: 1.5;
			font-weight: bold;
		}

		.card-address {
			font-size: 1rem;
			line-height: 1;
		}

		.card-link > button {
			color: #9acac3;
			font-weight: 500;
			font-size: 1rem;
			margin: 1rem;
			text-transform: uppercase;
		}
	}
}
</style>
