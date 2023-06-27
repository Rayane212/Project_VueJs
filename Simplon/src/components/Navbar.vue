<script setup>
import IconLogoVue from "./icons/IconLogo.vue";
import IconProfileVue from "./icons/IconProfile.vue";
</script>

<template>
  <nav class="container-fluid mt-1">
    <div
      class="container pt-1 pb-4 d-flex justify-content-between align-items-center bg-light border border-dark rounded rounded-4">
      <a class="navbar-brand" href="#">
        <IconLogoVue class="me-2" />
      </a>
      <div class="flex-grow-1 text-center">
        <h3 class="Playfair-Display-title">Mon réseau</h3>
      </div>
      <a class="ms-auto">
        <IconProfileVue />
      </a>
    </div>
  </nav>
</template>
<style></style>