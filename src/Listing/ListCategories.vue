<template>
  <div class="row">
    <div class="col-1" v-for="(category, index) in categories" :key="index">
      <button type="button" class="btn" @click="goToProduct(category)">{{ category }}</button>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      categories: [],
    };
  },
  mounted() {
    this.getCategories();
  },
  methods: {
    getCategories() {
      axios
        .get("http://37.187.244.116:5000/categories", {
          headers: {
            "Access-Control-Allow-Origin": "*",
            "Content-type": "application/json",
          },
        })
        .then((response) => (this.categories = response.data));
    },
    goToProduct($category) {
     window.location.href ="/products/"+$category;
    },
  },
};
</script>
