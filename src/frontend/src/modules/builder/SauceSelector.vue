<template>
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
</template>
<script>
import RadioButton from "@/common/components/RadioButton.vue";

export default {
  name: "SauceSelector",
  props: {
    sauce: {
      type: Array,
      required: true,
    },
  },
  components: {
    RadioButton,
  },
  methods: {
    changeSauce(index) {
      this.$emit("changeSauce", index);
    },
  },
};
</script>
<style></style>
