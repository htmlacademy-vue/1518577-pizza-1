<template lang="">
  <div class="ingredients__filling">
    <p>Начинка:</p>

    <ul class="ingredients__list">
      <ItemCounter
        v-for="(fillingItem, index) in filling"
        :key="fillingItem.id"
        :name="fillingItem.name"
        :value="fillingItem.value"
        @click="addFilling(index, -1)"
        ><AppDrag :transferData="filling" />
      </ItemCounter>
    </ul>
  </div>
</template>
<script>
import ItemCounter from "@/common/components/ItemCounter.vue";
import AppDrag from "@/common/components/AppDrag.vue";

export default {
  name: "FillingSelector",
  components: {
    ItemCounter,
    AppDrag,
  },
  props: {
    filling: {
      type: Array,
      required: true,
    },
  },
  methods: {
    addFilling(index, value) {
      this.$emit("addFilling", index, value);
    },
  },
};
</script>
<style lang=""></style>
