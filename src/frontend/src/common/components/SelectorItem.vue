<template lang="">
  <label :class="itemClass">
    <input
      type="radio"
      :name="itemName"
      :value="value"
      class="visually-hidden"
      :checked="value"
    />
    <b>{{ name }}</b>
    <span> {{ description }}</span>
  </label>
</template>
<script>
export default {
  name: "SelectorItem",
  props: {
    name: {
      type: String,
      required: false,
    },
    value: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: false,
    },
    itemClass: {
      type: String,
      required: true,
    },
    itemChecked: {
      type: String,
      required: false,
    },
    itemName: {
      type: String,
      required: true,
    },
  },
};
</script>
<style lang=""></style>
