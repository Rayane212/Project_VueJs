<script setup>
import { RouterLink, RouterView } from "vue-router";
import IconFacebookVue from "./icons/IconFacebook.vue";
import IconProfileVue from "./icons/IconProfile.vue";
</script>

<template>
  <nav class="container-fluid">
    <div
      class="container mt-1 d-flex justify-content-between align-items-center"
    >
      <a class="navbar-brand" href="#">
        <IconFacebookVue class="me-2" />
      </a>
      <div class="flex-grow-1 text-center">
        <h3>Mon réseau</h3>
      </div>
      <a class="ms-auto">
        <IconProfileVue />
      </a>
    </div>
  </nav>
</template>

<style></style>
