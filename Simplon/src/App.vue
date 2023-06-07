<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/Navbar.vue'
import AddFriends from "./components/AddFriends.vue";
import FilterAndSearch from './components/FilterAndSearch.vue';

</script>

<template>
  <header>
      <Navbar />
  </header>
  <body>
    <AddFriends/>
    <FilterAndSearch/>
  </body>
    
</template>

<style scoped></style>
