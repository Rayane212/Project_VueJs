<script setup>
import IconLogoVue from "./icons/IconLogo.vue";
import IconProfileVue from "./icons/IconProfile.vue";
</script>

<template>
  <nav class="container-fluid ">
    <div class="container pt-1 pb-4 d-flex justify-content-between align-items-center bg-light">
      <a class="navbar-brand" href="#">
        <IconLogoVue class="me-2" />
      </a>
      <div class="flex-grow-1 text-center">
        <h3 class="elegantaria-title">Mon réseau</h3>      
      </div>
      <a class="ms-auto">
        <IconProfileVue />
      </a>
    </div>
  </nav>
</template>
<style>
.elegantaria-title {
  font-family: 'Playfair Display', serif;
  font-weight: bold;
  color: #48466d;
}

</style>