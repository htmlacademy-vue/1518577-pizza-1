<template>
  <div>
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <DoughSelector
            :dough="dough"
            @updatePizza="updatePizzaDough"
            @changeDough="changeDough"
          />
          <SizeSelector :size="size" @changeSize="changeSize" />
          <h1>{{ pizzaDough }}</h1>
          <IngredientsSelector
            :ingredient="ingredient"
            :sauce="sauce"
            @addIngredient="addIngredient"
            @changeSauce="changeSauce"
          />
          <PizzaView />
        </div>
      </form>
    </main>
  </div>
</template>
<script>
import pizza from "@/static/pizza.json";
import DoughSelector from "@/modules/builder/DoughSelector.vue";
import IngredientsSelector from "@/modules/builder/IngredientsSelector.vue";
import SizeSelector from "@/modules/builder/SizeSelector.vue";
import PizzaView from "@/modules/builder/PizzaView.vue";

import {
  extendValue,
  doughTypes,
  sizeTypes,
  sauceTypes,
  ingredientTypes,
} from "@/common/helper.js";

export default {
  name: "IndexPage",
  data() {
    return {
      pizzaDough: "",
      pizzas: pizza,
      dough: pizza.dough.map((item) => extendValue(item, doughTypes)),
      size: pizza.sizes.map((item) => extendValue(item, sizeTypes)),
      sauce: pizza.sauces.map((item) => extendValue(item, sauceTypes)),
      ingredient: pizza.ingredients.map((item) =>
        extendValue(item, ingredientTypes)
      ),
    };
  },
  components: {
    DoughSelector,
    IngredientsSelector,
    SizeSelector,
    PizzaView,
  },
  methods: {
    updatePizzaDough(someData) {
      this.pizzaDough = someData.pizzaDough;
    },
    changeDough(index) {
      for (let i = 0; i < this.dough.length; i++) {
        this.dough[i].checked = i === index;
      }
    },
    changeSize(index) {
      for (let i = 0; i < this.size.length; i++) {
        this.size[i].checked = i === index;
      }
    },
    changeSauce(index) {
      for (let i = 0; i < this.sauce.length; i++) {
        this.sauce[i].checked = i === index;
      }
    },
    addIngredient(index, value) {
      this.ingredient[index].count = this.ingredients[index].count + value;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/app.scss";
</style>
