<template>
  <div>
    <header class="header">
      <div class="header__logo">
        <a href="index.html" class="logo">
          <img :src="logo" alt="V!U!E! Pizza logo" width="90" height="40" />
        </a>
      </div>
      <div class="header__cart">
        <a href="cart.html">0 ₽</a>
      </div>
      <div class="header__user">
        <a href="#" class="header__login"><span>Войти</span></a>
      </div>
    </header>

    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>

          <div class="content__dough">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите тесто</h2>

              <div
                class="sheet__content dough"
                v-for="dough in pizzas.dough"
                :key="dough.id"
              >
                <label :class="`dough__input dough__input--${dough.value}`">
                  <input
                    type="radio"
                    name="dought"
                    :value="dough.value"
                    class="visually-hidden"
                    :checked="dough.value === 'light'"
                  />
                  <b>{{ dough.name }}</b>
                  <span> {{ dough.description }}</span>
                </label>
              </div>
            </div>
          </div>

          <div class="content__diameter">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите размер</h2>

              <div
                v-for="size in pizzas.sizes"
                :key="size.id"
                class="sheet__content diameter"
              >
                <label
                  :class="`diameter__input diameter__input--${size.value}`"
                >
                  <input
                    type="radio"
                    name="diameter"
                    :value="size.value"
                    class="visually-hidden"
                    :checked="size.value === 'normal'"
                  />
                  <span>{{ size.name }}</span>
                </label>
              </div>
            </div>
          </div>

          <div class="content__ingredients">
            <div class="sheet">
              <h2 class="title title--small sheet__title">
                Выберите ингредиенты
              </h2>

              <div class="sheet__content ingredients">
                <div class="ingredients__sauce">
                  <p>Основной соус:</p>

                  <label
                    v-for="sauce in pizzas.sauces"
                    :key="sauce.id"
                    class="radio ingredients__input"
                  >
                    <input
                      type="radio"
                      name="sauce"
                      :value="sauce.value"
                      :checked="sauce.value === 'tomato'"
                    />
                    <span>{{ sauce.name }}</span>
                  </label>
                </div>

                <div class="ingredients__filling">
                  <p>Начинка:</p>

                  <ul
                    v-for="ingredient in pizzas.ingredients"
                    :key="ingredient.id"
                    class="ingredients__list"
                  >
                    <li class="ingredients__item">
                      <span :class="`filling filling--${ingredient.value}`">{{
                        ingredient.name
                      }}</span>

                      <div class="counter counter--orange ingredients__counter">
                        <button
                          type="button"
                          class="counter__button counter__button--minus"
                          disabled
                        >
                          <span class="visually-hidden">Меньше</span>
                        </button>
                        <input
                          type="text"
                          name="counter"
                          class="counter__input"
                          value="0"
                        />
                        <button
                          type="button"
                          class="counter__button counter__button--plus"
                        >
                          <span class="visually-hidden">Больше</span>
                        </button>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <div class="content__pizza">
            <label class="input">
              <span class="visually-hidden">Название пиццы</span>
              <input
                type="text"
                name="pizza_name"
                placeholder="Введите название пиццы"
              />
            </label>

            <div class="content__constructor">
              <div class="pizza pizza--foundation--big-tomato">
                <div class="pizza__wrapper">
                  <div class="pizza__filling pizza__filling--ananas"></div>
                  <div class="pizza__filling pizza__filling--bacon"></div>
                  <div class="pizza__filling pizza__filling--cheddar"></div>
                </div>
              </div>
            </div>

            <div class="content__result">
              <p>Итого: 0 ₽</p>
              <button type="button" class="button" disabled>Готовьте!</button>
            </div>
          </div>
        </div>
      </form>
    </main>
  </div>
</template>
<script>
import pizza from "@/static/pizza.json";
import logo from "@/assets/img/logo.svg";

export default {
  name: "IndexPage",
  data() {
    return {
      pizzas: pizza,
      logo: logo,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/app.scss";
</style>
