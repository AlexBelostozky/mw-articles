<template>
  <li class="mArticle">
    <article class="mArticle__wrapper">
      <picture class="mArticle__thumbnail">
          <source media="(min-width: 1440px)" srcset="../assets/img/header/magwai-logo.svg" width="320" height="185">
					<source media="(min-width: 768px)" srcset="../assets/img/header/magwai-logo.svg" width="334" height="185">
					<img :src="articleData.image" width="329" height="185" :alt="articleData.altText">
			</picture>

      <div class="mArticle__content-wrapper">
        <span class="mArticle__theme">
          {{ articleData.theme ? articleData.theme : 'Some topic' }}
        </span>

        <h3 class="mArticle__title">
          {{ articleData.title }}
        </h3>

        <p class="mArticle__description">
          {{ articleData.body }}
        </p>

        <span class="mArticle__info">
          Posted by

          <b>
            {{ articleData.author ? articleData.author : 'Someone' }}
          </b>, on

          <time
            class="mArticle__date"
            :datetime="formatRewievDate(articleData.date).datetime"
          >
            {{ articleData.date ? formatRewievDate(articleData.date).formattedDate : 'Sometime'}}
          </time>
        </span>

        <a class="mArticle__button" href="#">
          Continue reading
        </a>
      </div>
    </article>
  </li>
</template>

<script>
import moment from "moment";

export default {
  name: 'mArticles',

  data () {
    return {

    }
  },

  props: {
    articleData: {}
  },

  methods: {
    formatRewievDate(date) {
      return {
        datetime: moment(date).format('YYYY-MM-DD'),
        formattedDate: moment(date).format('MMMM D, YYYY')
      }
    }
  }
}


</script>

<style lang="scss">
@import "../assets/globalStyles/styles.scss";

.mArticle {
  background-color: $white;
  color: $black;
  margin: 0;
}

.mArticle__thumbnail img {
  display: block;
  width: 100%;
  object-fit: cover;
  object-position: center;
}

.mArticle__content-wrapper {
  padding: 25px 24px 30px;
}

.mArticle__theme {
  display: block;
  font-family: "Mulish", "Arial", sans-serif;
  font-weight: 700;
  font-size: 14px;
  line-height: 26px;
  text-transform: uppercase;
  letter-spacing: 1.5px;
  margin: 0;
	margin-bottom: 20px;
}

.mArticle__title {
  font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 26px;
  margin: 0;
	margin-bottom: 20px;

  &::first-letter {
    text-transform: capitalize;
  }
}

.mArticle__description {
  font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  color: $gray;
  max-height: 144px;
  margin: 0;
	margin-bottom: 20px;
  overflow: hidden;
  text-overflow: ellipsis;

  &::first-letter {
    text-transform: capitalize;
  }
}

.mArticle__info {
  display: block;
  font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 400;
  font-size: 12px;
  line-height: 24px;
  color: $gray;
  margin-bottom: 20px;
}

.mArticle__button {
  box-sizing: border-box;
  display: block;
  font-family: "Mulish", "Arial", sans-serif;
  font-weight: 600;
  font-size: 14px;
  line-height: normal;
  color: $white;
  text-align: center;
  text-decoration: none;
  background-color: $gray-dark;
  width: 100%;
  min-height: 50px;
  padding: 13px;
  border: 3px solid $gray-dark;
  transition: all 0.2s ease-in-out;

  &:hover,
  &:focus {
    color: $black;
    background-color: $white;
  }

  &:active {
    color: $white;
    background-color: $gray-light;
    border-color: $gray-light;
  }
}
</style>
