<template>
  <li class="mArticle">
    <article class="mArticle__wrapper">
      <picture class="mArticle__thumbnail">
          <source media="(min-width: 1440px)" srcset="../assets/img/header/magwai-logo.svg" width="320" height="185">
					<source media="(min-width: 768px)" srcset="../assets/img/header/magwai-logo.svg" width="334" height="185">
					<img :src="articleData.image" width="329" height="185" :alt="articleData.altText">
			</picture>

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

</style>
