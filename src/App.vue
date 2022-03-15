<template>

  <div id="app">
  

  <nav class="navbar navbar-expand-lg navbar navbar-dark bg-dark">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Gestion des prix </a>
    </div>
  </nav>


    <ListCategories />
  </div>
</template>

<script>
import ListCategories from "./Listing/ListCategories.vue";

export default {
  name: "App",
  components: {
    ListCategories,
   
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
</style>
