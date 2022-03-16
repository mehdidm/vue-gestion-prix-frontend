<template>
  <div class="row">
    <p>ici produits</p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    this.getProducts();
  },
  methods: {
    getProducts() {
      axios
        .get("http://37.187.244.116:5000/products/"+this.$route.params.category, {
          headers: {
            "Access-Control-Allow-Origin": "*",
            "Content-type": "application/json",
          },
        })
        .then((response) => (this.products = response.data));
    },
  },
};
</script>
