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

</style>
