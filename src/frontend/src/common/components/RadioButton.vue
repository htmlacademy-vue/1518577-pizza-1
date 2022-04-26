<template lang="">
  <label class="radio ingredients__input">
    <input
      type="radio"
      name="sauce"
      :value="value"
      :checked="value === 'tomato'"
    />
    <span>{{ name }}</span>
  </label>
</template>
<script>
export default {
  name: "RadioButton",
  props: {
    value: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
  },
};
</script>
<style lang=""></style>
