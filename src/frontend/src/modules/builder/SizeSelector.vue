<template>
  <div class="content__diameter">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите размер</h2>
      <div class="sheet__content diameter">
        <label
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
        </label>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "SizeSelector",
  props: {
    size: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    changeSize(index) {
      this.$emit("changeSize", index);
    },
  },
};
</script>
<style lang=""></style>
