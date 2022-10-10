<template lang="">
  <div class="content__ingredients">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>

      <div class="sheet__content ingredients">
        <div class="ingredients__sauce">
          <p>Основной соус:</p>
          <RadioButton
            v-for="(sauceItem, index) in sauce"
            :key="sauceItem.id"
            :value="sauceItem.value"
            :name="sauceItem.name"
            @change="changeSauce(index)"
          />
        </div>

        <div class="ingredients__filling">
          <p>Начинка:</p>

          <ul class="ingredients__list">
            <ItemCounter
              v-for="(ingredientItem, index) in ingredient"
              @input="$emit('input', pizzaIngredients)"
              :key="ingredientItem.id"
              :name="ingredientItem.name"
              :classValue="ingredientItem.value"
              :min="0"
              :max="MAX_INGREDIENT_COUNT"
              :ingredient="ingredient"
              @click="addIngredient(index, -1)"
            />
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import RadioButton from "@/common/components/RadioButton.vue";
import ItemCounter from "@/common/components/ItemCounter.vue";
// import AppDrag from "@/common/components/AppDrag.vue";
import { MAX_INGREDIENT_COUNT } from "@/common/constants";

export default {
  name: "IngredientsSelector",
  props: {
    ingredient: {
      type: Array,
      required: true,
    },
    sauce: {
      type: Array,
      required: true,
    },
  },
  data() {
    return { MAX_INGREDIENT_COUNT };
  },
  components: {
    RadioButton,
    ItemCounter,
  },
  methods: {
    changeSauce(index) {
      this.$emit("changeSauce", index);
    },
    addIngredient(index, value) {
      this.$emit("addIngredient", index, value);
    },
  },
};
</script>
<style></style>
