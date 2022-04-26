<template>
  <div class="content__pizza">
    <label class="input">
      <span class="visually-hidden">Название пиццы</span>
      <input
        type="text"
        name="pizza_name"
        placeholder="Введите название пиццы"
      />
    </label>
    <AppDrop>
      <div class="content__constructor">
        <div class="pizza pizza--foundation--big-tomato">
          <div class="pizza__wrapper">
            <div class="pizza__filling pizza__filling--ananas"></div>
            <div class="pizza__filling pizza__filling--bacon"></div>
            <div class="pizza__filling pizza__filling--cheddar"></div>
          </div>
        </div>
      </div>
    </AppDrop>
    <PriceCounter />
  </div>
</template>
<script>
import PriceCounter from "@/modules/builder/PriceCounter.vue";
import AppDrop from "@/common/components/AppDrop.vue";

export default {
  name: "PizzaView",
  components: {
    PriceCounter,
    AppDrop,
  },
};
</script>
<style lang=""></style>
