<template>
	<section class="mArticles">
		<div class="mArticles__wrapper">
			<h2 class="mArticles__title">
				Карточки
			</h2>

			<ul
				class="mArticles__list"
				v-for="article in articlesList"
				:key="article.id"
			>
				<mArticle :articleData="article" />
			</ul>
		</div>

		<a class="mArticles__button" href="#">
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
      articlesList: [
        {
          "userId": 1,
          "id": 1,
          "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
          "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto",
          "image": "https://via.placeholder.com/150/92c952",
          "alt": "Alt"
        },
        {
          "userId": 1,
          "id": 2,
          "title": "qui est esse",
          "body": "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla",
          "image": "https://via.placeholder.com/150/92c952",
          "alt": "Alt"
        },
        {
          "userId": 1,
          "id": 3,
          "title": "ea molestias quasi exercitationem repellat qui ipsa sit aut",
          "body": "et iusto sed quo iure\nvoluptatem occaecati omnis eligendi aut ad\nvoluptatem doloribus vel accusantium quis pariatur\nmolestiae porro eius odio et labore et velit aut",
          "image": "https://via.placeholder.com/150/92c952",
          "alt": "Alt"
        },
      ]
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
}

.mArticles__wrapper {
	width: 92%;
	margin: 0 auto;

	@media (min-width: $tablet-width) {
		width: 87%;
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
}

.mArticles__list {
	list-style: none;
	margin: 0;
	margin-bottom: 38px;
	padding: 0;

	@media (min-width: $tablet-width) {
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

	@media (min-width: $tablet-width) {
		width: 281px;
    min-height: 60px;
    padding: 21px;
  }

	@media (min-width: $desktop-width) {
		margin-left: 1%;
	}
}

.mArticles__button-text {
	display: block;
	transform: skewX(19deg);
}
</style>
