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
            <AppDrag :transferData="ingredient">
              <ItemCounter
                v-for="(ingredientItem, index) in ingredient"
                :key="ingredientItem.id"
                :name="ingredientItem.name"
                :value="ingredientItem.value"
                @click="addIngredient(index, -1)"
              />
            </AppDrag>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import RadioButton from "@/common/components/RadioButton.vue";
import ItemCounter from "@/common/components/ItemCounter.vue";
import AppDrag from "@/common/components/AppDrag.vue";

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
  components: {
    RadioButton,
    ItemCounter,
    AppDrag,
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
