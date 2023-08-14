<template>
  <main class="mMain">
    <div class="mMain__wrapper">
      <section class="hero">
        <div class="hero__wrapper">
          <div class="hero__content-wrapper">
            <h1 class="hero__title">
            Полет Илона Маска<br>
            и DOGIE COIN
          </h1>

          <p class="hero__description">
            В прошлый четверг все офигели от полета DOGIE COIN на марс.
          </p>

          <a class="hero__request-button" href="#">
            <span class="hero__request-button-text">
              Оставить заявку
            </span>
          </a>
          </div>
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

  @media (min-width: $tablet-width) {
    margin-top: 117px;
  }
}

.hero {
  position: relative;
  height: calc(100vh - 72px);
  background-image: image-set(url("../assets/img/main/hero-mobile.jpg") 1x, url("../assets/img/main/hero-mobile@2x.jpg") 2x);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 30px 30px 0 0;

  @media (min-width: $tablet-width) {
    height: calc(100vh - 117px);
    background-image: image-set(url("../assets/img/main/hero-tablet.jpg") 1x, url("../assets/img/main/hero-tablet@2x.jpg") 2x);
  }

  @media (min-width: $desktop-width) {
    background-image: image-set(url("../assets/img/main/hero-desktop.jpg") 1x, url("../assets/img/main/hero-desktop@2x.jpg") 2x);
  }
}

.hero__wrapper {
  position: absolute;
  right: 0;
  left: 0;
  bottom: 0;
  padding: 52px 0 52px;
  background-image: linear-gradient(0deg, $black 0%, transparent 100%);
}

.hero__content-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  gap: 20px;
  width: 92%;
  margin: 0 auto;

  @media (min-width: $tablet-width) {
    gap: 40px;
    width: 87%;
  }

  @media (min-width: $desktop-width) {
    width: 90%;
  }
}

.hero__title {
  font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 700;
  font-size: 20px;
  line-height: normal;
  text-transform: uppercase;
  margin: 0;

  @media (min-width: $tablet-width) {
    font-size: 38px;
  }

  @media (min-width: $desktop-width) {
    font-size: 42px;
  }
}

.hero__description {
  color: $white-80;
  margin: 0;

  @media (min-width: $tablet-width) {
    font-size: 16px;
    line-height: 24px;
    max-width: 460px;
  }
}

.hero__request-button {
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
	width: 206px;
	min-height: 47px;
	padding: 14px;
  margin-left: 2%;
  margin-right: auto;
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

.hero__request-button-text {
	display: block;
	transform: skewX(19deg);
}
</style>
