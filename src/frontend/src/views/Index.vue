<template>
  <div>
    <div v-for="misc in miscs" :key="misc.id">
      {{ misc }}
    </div>
    <div v-for="pizza in pizzas" :key="pizza.id">
      {{ pizza }}
    </div>
    <div v-for="user in users" :key="user.id">
      {{ user }}
    </div>
  </div>
</template>
<script>
import misc from "@/static/misc.json";
import pizza from "@/static/pizza.json";
import user from "@/static/user.json";

export default {
  name: "IndexPage",
  data() {
    return {
      miscs: misc,
      pizzas: pizza,
      users: user,
    };
  },
};
</script>
