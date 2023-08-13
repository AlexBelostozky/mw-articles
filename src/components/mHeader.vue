<template>
	<header class="mHeader" ref="headerElement">
		<div class="mHeader__wrapper">
			<a class="mHeader__logo" href="#">
				<picture>
					<source media="(min-width: 768px)" srcset="../assets/img/header/magwai-logo.svg" width="156" height="60">
					<img src="../assets/img/header/magwai-logo.svg" width="112" height="38" alt="Логотип Magwai.">
				</picture>
			</a>

			<nav class="mHeader__navigation">
				<div class="mHeader__navigation-button">
					<label class="mHeader__navigation-button-label visually-hidden" for="navigation-checkbox">
						<span class="visually-hidden">
							Открыть/закрыть меню
						</span>
					</label>

					<input
						class="mHeader__navigation-toggle"
						type="checkbox"
						id="navigation-checkbox"
						ref="navigationCheckbox"
						@change="onNavigationToggleChange"
					>

					<div class="mHeader__navigation-hamburger">
            <span class="mHeader__navigation-hamburger-line mHeader__navigation-hamburger-line--1"></span>
            <span class="mHeader__navigation-hamburger-line mHeader__navigation-hamburger-line--2"></span>
            <span class="mHeader__navigation-hamburger-line mHeader__navigation-hamburger-line--3"></span>
          </div>
				</div>

				<ul class="mHeader__navigation-list">
					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							Услуги
						</a>
					</li>

					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							Абонементы
						</a>
					</li>

					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							Почему мы
						</a>
					</li>

					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							Оборудование
						</a>
					</li>

					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							Акции
						</a>
					</li>

					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							FAQ
						</a>
					</li>

					<li class="mHeader__navigation-item">
						<a class="mHeader__navigation-link" href="#">
							Контакты
						</a>
					</li>
				</ul>
			</nav>

			<div class="mHeader__buttons-wrapper">
				<a class="mHeader__call-button" href="tel:+79999999999">
					<span class="visually-hidden">
						Позвонить нам
					</span>

					<div class="mHeader__call-button-image"></div>
				</a>

				<a class="mHeader__request-button" href="#">
					<span class="mHeader__request-button-text">Оставить заявку</span>
				</a>
			</div>
		</div>
	</header>
</template>

<script>
import { ref } from 'vue';

export default {
	name: 'mHeader',
	props: {
	},

	setup() {
		const headerElement = ref(null);
		const navigationCheckbox = ref(null);

		return {
			headerElement,
			navigationCheckbox
		}
	},

	methods: {
		// Navigation
		onNavigationToggleChange() {
			this.toggleHeader();
		},

		toggleHeader() {
			this.headerElement.classList.toggle('mHeader--opened');
			document.body.classList.toggle('page__body--locked');
		}
	}
}
</script>

<style lang="scss">
@import "../assets/globalStyles/styles.scss";

.mHeader {
	position: fixed;
	top: 0;
	width: 100%;
	color: $white;
	background-color: $black;
	transition: all 0.2s ease-in-out;

	&--opened {
		height: 100vh;

		.mHeader__navigation-list,
		.mHeader__call-button,
		.mHeader__request-button  {
			visibility: visible;
			opacity: 1;
		}
	}
}

.mHeader__wrapper {
	display: flex;
	justify-content: space-between;
	align-items: center;
	min-height: 72px;
	width: 92%;
	margin: 0 auto;
}

.mHeader__logo {
	order: 2;
}

.mHeader__navigation {

}

.mHeader__navigation-button {
	position: relative;
	padding: 6px 3px;
}

.mHeader__navigation-toggle {
	display: block;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
	width: 37px;
	height: 37px;
	cursor: pointer;
  opacity: 0;
	z-index: 2;

	&:hover ~
	.mHeader__navigation-hamburger
	.mHeader__navigation-hamburger-line,
	&:focus ~
	.mHeader__navigation-hamburger
	.mHeader__navigation-hamburger-line {
		background-color: $pink;
	}

	&:active ~
	.mHeader__navigation-hamburger
	.mHeader__navigation-hamburger-line {
		background-color: $violet;
	}
}

.mHeader__navigation-hamburger {
	position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  width: 37px;
  height: 26px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: transform 0.4s ease-in-out;
  pointer-events: none;
}

.mHeader__navigation-hamburger-line {
	display: block;
  height: 3px;
  background: $white;
	border-radius: 10px;
	transition: all 0.2s ease-in-out;
	transform-origin: 0% 50%;

	&--1 {
		width: 50%;
	}

	&--2 {
		width: 100%;
	}

	&--3 {
		width: 75%;
	}
}

.mHeader__navigation-toggle:checked ~
.mHeader__navigation-hamburger
.mHeader__navigation-hamburger-line--1 {
	animation: hamburger1in 0.4s;
}

.mHeader__navigation-toggle:checked ~
.mHeader__navigation-hamburger
.mHeader__navigation-hamburger-line--2 {
	animation: hamburger2in 0.4s;
}

.mHeader__navigation-toggle:checked ~
.mHeader__navigation-hamburger
.mHeader__navigation-hamburger-line--3 {
	animation: hamburger3in 0.4s;
}

.mHeader__navigation-toggle:not(:checked) ~
.mHeader__navigation-hamburger
.mHeader__navigation-hamburger-line--1 {
	animation: hamburger1out 0.4s;
}

.mHeader__navigation-toggle:not(:checked) ~
.mHeader__navigation-hamburger
.mHeader__navigation-hamburger-line--2 {
	animation: hamburger2out 0.4s;
}

.mHeader__navigation-toggle:not(:checked) ~
.mHeader__navigation-hamburger
.mHeader__navigation-hamburger-line--3 {
	animation: hamburger3out 0.4s;
}

@keyframes hamburger1in {
  0% {
    width: 50%;
  }
	50% {
		width: 100%;
	}
  100% {
    width: 50%;
  }
}

@keyframes hamburger2in {
  0% {
    width: 100%;
  }
	50% {
		width: 50%;
	}
  100% {
    width: 100%;
  }
}

@keyframes hamburger3in {
  0% {
    width: 75%;
  }
	50% {
		width: 100%;
	}
  100% {
    width: 75%;
  }
}

@keyframes hamburger1out {
  0% {
    width: 50%;
  }
	50% {
		width: 100%;
	}
  100% {
    width: 50%;
  }
}

@keyframes hamburger2out {
  0% {
    width: 100%;
  }
	50% {
		width: 50%;
	}
  100% {
    width: 100%;
  }
}

@keyframes hamburger3out {
  0% {
    width: 75%;
  }
	50% {
		width: 100%;
	}
  100% {
    width: 75%;
  }
}

.mHeader__navigation-list {
	position: absolute;
	top: 71px;
	width: 92%;
	height: 60%;
	display: flex;
	flex-direction: column;
	gap: 15px;
	list-style: none;
	margin: 0 auto;
	padding: 0;
	visibility: hidden;
	opacity: 0;
	transition: all 0.2s ease-in-out;
}

.mHeader__navigation-item {
	font-family: "Montserrat", "Arial", sans-serif;
  font-weight: 700;
  font-size: 20px;
  line-height: 30px;
}

.mHeader__navigation-link {
	color: $black;
	text-decoration: none;
	transition: all .2s ease-in-out;
	text-transform: uppercase;
	-webkit-text-stroke: 1px $gray-light;

	&:hover,
	&:focus {
		-webkit-text-stroke-color: $pink;
		text-shadow: 0 0 1px $pink;
	}

	&:active {
		color: $violet;
		-webkit-text-stroke-color: $violet;
		text-shadow: 0 0 1px $violet;

	}
}

.mHeader__buttons-wrapper {
	position: fixed;
	bottom: 0;
	box-sizing: border-box;
	width: 92%;
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 6px;
	margin: 0 auto;
	padding-bottom: 15px;
}

.mHeader__call-button {
	position: relative;
	visibility: hidden;
	opacity: 0;
	display: block;
	box-sizing: border-box;
	// background-color: transparent;

	// background-color: $white-40;

	border: 1px solid $white-40;
	width: 93%;
	min-height: 60px;
	transform: skewX(-19deg);
	transition: all 0.2s ease-in-out;

	&::before {
		position: absolute;
		top: 50%;
		left: 50%;
		content: '';
		width: 32px;
		height: 32px;
		--svg: url('../assets/img/header/phone-icon.svg');
		-webkit-mask: var(--svg);
		mask: var(--svg);
		background-color: $white-40;
		background-position: center;
		background-repeat: no-repeat;
		background-size: cover;
		transform: skewX(19deg) translateX(-50%) translateY(-50%);
	}

	&:hover,
	&:focus {
		border-color: $white;

		&::before {
			background-color: $white;
		}
	}

	&:active {
		border-color: $gray-light;

		&::before {
			background-color: $gray-light;
		}
	}
}

.mHeader__request-button {
	visibility: hidden;
	opacity: 0;
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
	width: 93%;
	min-height: 60px;
	padding: 21px;
	transform: skewX(-19deg);
	transition: all 0.2s ease-in-out;

	&:hover,
	&:focus {
		background-color: $white;
		color: $black;
	}

	&:active {
		background-color: $gray-light;
		color: $black;
	}
}

.mHeader__request-button-text {
	display: block;
	transform: skewX(19deg);
}


</style>
