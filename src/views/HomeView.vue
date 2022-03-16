<template>
  <div class="home">
    <br />
  <h1>Liste des categories </h1>
    <br />
    <Categories/>
  </div>
</template>

<script>
// @ is an alias to /src
import Categories from '@/Listing/ListCategories.vue'

export default {
  name: 'HomeView',
  components: {
    Categories
  }
}
</script>
