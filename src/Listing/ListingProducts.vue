<template>
  <div class="row">
    <div class="col-1" v-for="(product, index) in products" :key="index">
     
    </div>
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
