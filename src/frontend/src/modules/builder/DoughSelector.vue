<template lang="">
  <div class="content__dough">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите тесто</h2>

      <div class="sheet__content dough">
        <SelectorItem
          v-for="(doughItem, index) in dough"
          :key="doughItem.id"
          :value="doughItem.value"
          :name="doughItem.name"
          :description="doughItem.description"
          :itemClass="`dough__input dough__input--${doughItem.value}`"
          :itemName="'dought'"
          @change="changeDough(index)"
          @click="changePizzaDough"
        />
      </div>
    </div>
  </div>
</template>
<script>
import SelectorItem from "@/common/components/SelectorItem.vue";

export default {
  name: "DoughSelector",
  data() {
    return {
      pizzaDough: "dough text",
    };
  },
  props: {
    dough: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  components: {
    SelectorItem,
  },
  methods: {
    changePizzaDough() {
      this.$emit("updatePizza", {
        pizzaDough: this.pizzaDough,
      });
    },
    changeDough(index) {
      this.$emit("changeDough", index);
    },
  },
};
</script>
<style lang=""></style>
