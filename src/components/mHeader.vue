<template>
	<header class="mHeader">
		<div class="mHeader__wrapper">
			<a class="mHeader__logo" href="#">
				<picture class="header-bottom__logo">
					<source media="(min-width: 768px)" srcset="../assets/img/header/magwai-logo.svg" width="156" height="60">
					<img src="../assets/img/header/magwai-logo.svg" width="112" height="38" alt="Логотип Magwai.">
				</picture>
			</a>

			<nav class="mHeader__navigation">
				<div class="mHeader__navigation-button">
					<label class="mHeader__navigation-button-label" for="navigation-checkbox">
						<span class="visually-hidden">
							Открыть/закрыть меню
						</span>
					</label>
					<input type="checkbox" id="navigation-checkbox">
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

			<a class="mHeader__call-button" href="tel:+79999999999">
				<span class="visually-hidden">
					Позвонить нам
				</span>
			</a>

			<a class="mHeader__request-button" href="#">
				Оставить заявку
			</a>
		</div>
	</header>
</template>

<script>
export default {
	name: 'mHeader',
	props: {
	}
}
</script>

<style lang="scss">

</style>
