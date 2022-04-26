<template>
  <div class="content__diameter">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите размер</h2>

      <div class="sheet__content diameter">
        <SelectorItem
          v-for="(sizeItem, index) in size"
          :key="sizeItem.id"
          :itemClass="`diameter__input diameter__input--${sizeItem.value}`"
          :value="sizeItem.value"
          :description="sizeItem.name"
          :itemName="'diameter'"
          :itemChecked="'normal'"
          @change="changeSize(index)"
        />
        <!-- <label
          v-for="sizeItem in size"
          :key="sizeItem.id"
          :class="`diameter__input diameter__input--${sizeItem.value}`"
        >
          <input
            type="radio"
            name="diameter"
            :value="sizeItem.value"
            class="visually-hidden"
            :checked="sizeItem.value === 'normal'"
          />
          <span>{{ sizeItem.name }}</span>
        </label> -->
      </div>
    </div>
  </div>
</template>
<script>
import SelectorItem from "@/common/components/SelectorItem.vue";

export default {
  name: "SizeSelector",
  props: {
    size: {
      type: Array,
      required: true,
    },
  },
  components: {
    SelectorItem,
  },
  methods: {
    changeSize(index) {
      this.$emit("changeSize", index);
    },
  },
};
</script>
<style lang=""></style>
