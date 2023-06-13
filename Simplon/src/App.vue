<script setup>
import HelloWorld from './components/HelloWorld.vue';
import Navbar from './components/Navbar.vue';
import AddFriends from "./components/AddFriends.vue";
import FilterAndSearch from './components/FilterAndSearch.vue';
import Cards from './components/Cards.vue';
import CardsGroupes from './components/CardsGroupes.vue';
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

<style></style>


<style scoped></style>
