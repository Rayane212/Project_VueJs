<script setup>
import { RouterLink, RouterView } from 'vue-router'
import IconFacebookVue from './icons/IconFacebook.vue';
import IconProfileVue from './icons/IconProfile.vue';
</script>
<template>
    <nav class="container-fluid">
        <div class="container mt-1">
            <a class="navbar-brand" href="#">
                <IconFacebookVue />
            </a>
            <a>
                <IconProfileVue />
            </a>
            <break />
            <div class="d-flex w-50 position-absolute end-0">
                <button class="btn btn-success me-2 " type="submit">ajouter ami / groupe </button>
                <button class="btn btn-success" type="submit">Invitation en attente</button>
            </div>
        </div>


    </nav>
</template>

<style></style>