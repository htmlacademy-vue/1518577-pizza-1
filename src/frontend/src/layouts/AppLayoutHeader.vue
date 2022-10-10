<template lang="">
  <header class="header">
    <div class="header__logo">
      <a href="index.html" class="logo">
        <img :src="logo" alt="V!U!E! Pizza logo" width="90" height="40" />
      </a>
    </div>
    <div class="header__cart">
      <a href="cart.html">0 ₽</a>
    </div>
    <div class="header__user">
      <a href="#" class="header__login"><span>Войти</span></a>
    </div>
  </header>
</template>
<script>
import logo from "@/assets/img/logo.svg";

export default {
  name: "AppLayoutHeader",
  data() {
    return {
      logo: logo,
    };
  },
};
</script>
<style lang=""></style>
