<template>
	<section class="mArticles">
		<div class="mArticles__wrapper">
			<h2 class="mArticles__title">
				Карточки
			</h2>

			<ul class="mArticles__list">
				<mArticle
					v-for="article in articlesList"
					:key="article.id"
					:articleData="article"
				/>
			</ul>
		</div>

		<a
			class="mArticles__button"
			href="#"
			@click.prevent="onArticlesButtonClick"
			v-if="this.prevPostsCount < this.maxPostsCount"
		>
			<span class="mArticles__button-text">
				Загрузить ещё
			</span>
		</a>
	</section>
</template>

<script>
import mArticle from './mArticle.vue'

export default {
  name: 'mArticles',
  components: {
    mArticle
  },

  data () {
    return {
			requestPostUrl: 'https://jsonplaceholder.typicode.com/posts',
			requestPhotoUrl: 'https://api.slingacademy.com/v1/sample-data/photos',
			requestUserUrl: 'https://jsonplaceholder.typicode.com/users',
			prevPostsCount: null,
			maxPostsCount: 30,
      articlesList: []
    }
  },

	mounted() {
		this.getSomePosts(this.articlesList.length + 1, this.articlesList.length + 5);
	},

	methods: {
		async getPost(postId) {
			try {
				// get post
				const postData = await fetch(this.requestPostUrl + '/' + postId);
				const post = await postData.json();
				// get photo
				const	photoData = await fetch(this.requestPhotoUrl + '/' + postId);
				const photo = await photoData.json();
				// get user
				const	userData = await fetch(this.requestUserUrl + '/' + post.userId);
				const user = await userData.json();
				// consolidate data
				post.image = await photo.photo.url;
				post.altText = await photo.photo.description;
				post.author = await user.name;
				return post
			} catch (error) {
				console.log(error);
			}
		},

		getSomePosts(prev, nextMax) {
			for (let idx = prev; idx <= nextMax; idx++) {
				this.getPost(idx)
				.then(article => this.articlesList.push(article));
			}
			this.prevPostsCount = nextMax;
		},

		onArticlesButtonClick() {
			const freeSlotsCount = this.maxPostsCount - this.prevPostsCount;

			if (freeSlotsCount >= 5) {
				this.prevPostsCount++;
				this.getSomePosts(this.prevPostsCount, this.prevPostsCount + 4);
			} else {
				this.prevPostsCount++;
				this.getSomePosts(this.prevPostsCount, this.prevPostsCount + freeSlotsCount - 1);
			}
		}
	}
}
</script>

<style lang="scss">
@import "../assets/globalStyles/styles.scss";

.mArticles {
	padding: 48px 0 43px;

	@media (min-width: $tablet-width) {
		padding: 44px 0 156px;
  }

	@media (min-width: $desktop-width) {
		padding: 134px 0 256px;
  }
}

.mArticles__wrapper {
	width: 92%;
	margin: 0 auto;

	@media (min-width: $tablet-width) {
		width: 87%;
  }

	@media (min-width: $desktop-width) {
		width: 90%;
  }
}

.mArticles__title {
	font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 700;
  font-size: 20px;
  line-height: normal;
  text-transform: uppercase;
  margin: 0;
	margin-bottom: 30px;

	@media (min-width: $tablet-width) {
		font-size: 42px;
		margin-bottom: 40px;
  }

	@media (min-width: $desktop-width) {
		margin-bottom: 53px;
  }
}

.mArticles__list {
	display: grid;
	grid-template-columns: repeat(auto-fill, minmax(293px, 1fr));
	gap: 20px 20px;
	list-style: none;
	margin: 0;
	margin-bottom: 38px;
	padding: 0;

	@media (min-width: $tablet-width) {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(293px, 1fr));
		gap: 30px 30px;
		margin-bottom: 60px;
  }
}

.mArticles__button {
	display: block;
	box-sizing: border-box;
	font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 700;
  font-size: 12px;
  line-height: 18px;
	text-decoration: none;
	text-transform: uppercase;
	text-align: center;
	color: $white;
	background-color: $gold;
	width: 264px;
	min-height: 60px;
	padding: 21px;
  margin: 0 auto;
	transform: skewX(-19deg);
	transition: all 0.2s ease-in-out;

  &::after {
		position: absolute;
		right: 0;
		top: 0;
		content: '';
		width: 6px;
		height: 100%;
		background-color: $white;
		transform: translateX(11px);
		transition: all 0.2s ease-in-out;
	}

	&:hover,
	&:focus {
		background-color: $white;
		color: $black;

		&::after {
			background-color: $gold;
			transform: translateX(15px);
		}
	}

	&:active {
		background-color: $gray-light;
		color: $black;

		&::after {
			background-color: $gold;
			transform: translateX(15px);
		}
	}
}

.mArticles__button-text {
	display: block;
	transform: skewX(19deg);
}
</style>
