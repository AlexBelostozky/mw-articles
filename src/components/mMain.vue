<template>
  <main class="mMain">
    <div class="mMain__wrapper">
      <section class="hero">
        <div class="hero__wrapper">
          <h1 class="hero__title">
            Полет Илона Маска<br>
            и DOGIE COIN
          </h1>

          <p class="hero__description">
            В прошлый четверг все офигели от полета DOGIE COIN на марс.
          </p>

          <a class="hero__request-button" href="#">
            Оставить заявку
          </a>
        </div>
      </section>

      <mArticles />
    </div>
  </main>
</template>

<script>
import mArticles from './mArticles.vue'

export default {
  name: 'mMain',
  components: {
    mArticles
  }
}
</script>

<style lang="scss">
@import "../assets/globalStyles/styles.scss";

.mMain {
  margin-top: 72px;

  // &::before {
  //   content: "";
  //   display: block;
  //   height: 72px;
  //   // margin-top: -72px;
  // }

  @media (min-width: $tablet-width) {
    margin-top: 117px;
  }
}

.hero{

}
</style>
