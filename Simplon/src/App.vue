<script setup>
import Navbar from './components/Navbar.vue';
import HomeView from './views/HomeView.vue';
</script>

<template>
    <div>
        <header>
            <Navbar />
        </header>
        <main>
           <HomeView/> 
        </main>
    </div>
</template>

<style scoped></style>
