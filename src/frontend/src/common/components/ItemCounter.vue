<template lang="">
  <li class="ingredients__item">
    <AppDrag
      :transferData="{}"
      :active="ingredient.count < MAX_INGREDIENT_COUNT"
    >
      <span :class="`filling filling--${classValue}`">
        {{ name }}
      </span>
    </AppDrag>
    <div class="counter counter--orange ingredients__counter">
      <button
        type="button"
        class="counter__button counter__button--minus"
        @click="addValue(-1 * step)"
        :disabled="value < 1"
      >
        <span class="visually-hidden">Меньше</span>
      </button>
      <input
        type="text"
        name="counter"
        class="counter__input"
        :value="value"
        @input="setValue($event.target.value)"
      />
      <button
        type="button"
        class="counter__button counter__button--plus"
        @click="addValue(step)"
      >
        <span class="visually-hidden">Больше</span>
      </button>
    </div>
  </li>
</template>
<script>
// import { MAX_INGREDIENT_COUNT } from '@/common/constants.js';
import AppDrag from "@/common/components/AppDrag.vue";
export default {
  name: "ItemCounter",
  components: {
    AppDrag,
  },
  props: {
    name: {
      type: String,
      required: true,
    },
    ingredient: {
      type: Array,
      required: true,
    },
    classValue: {
      type: String,
      required: true,
    },
    quantityValue: {
      type: Number,
      default: 0,
    },
    max: {
      type: Number,
      default: 0,
    },
    min: {
      type: Number,
      default: 0,
    },
    step: {
      type: Number,
      default: 1,
    },
  },
  data() {
    return {
      value: this.quantityValue,
    };
  },
  methods: {
    setValue(value = 0) {
      !value && (value = 0);
      value = parseInt(value);
      if (value !== this.value) this.$emit("input", value);
      this.$forceUpdate(); // for case when user enters value greater than max
    },
    fitLimits(value) {
      if (value < this.min) value = this.min;
      if (value > this.max) value = this.max;
      return value;
    },
    addValue(value = 0) {
      const newValue = this.fitLimits(this.value + value);
      if (newValue !== this.value) this.$emit("input", newValue);
      this.value = this.value + 1;
      return this.value;
    },
  },
};
</script>
