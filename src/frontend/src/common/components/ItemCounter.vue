<template lang="">
  <li class="ingredients__item">
    <span :class="`filling filling--${value}`">{{ name }}</span>

    <div class="counter counter--orange ingredients__counter">
      <button
        type="button"
        class="counter__button counter__button--minus"
        disabled
      >
        <span class="visually-hidden">Меньше</span>
      </button>
      <input type="text" name="counter" class="counter__input" value="0" />
      <button type="button" class="counter__button counter__button--plus">
        <span class="visually-hidden">Больше</span>
      </button>
    </div>
  </li>
</template>
<script>
export default {
  name: "ItemCounter",
  props: {
    name: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
  },
};
</script>
<style lang=""></style>
