<template>
  <div class="tab1">
    <table class="table table-hover product-table mx-auto">
      <thead>
        <tr>
          <th>ID</th>
          <th>Image</th>
          <th>Description</th>
          <th>Prix</th>
          <th>Détails</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product" track-by="id">
          <td>{{ product.id }}</td>
          <td><img :src="apiImage+product.media"  class="imgProduct"/></td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
          <td>
            <button
              type="button"
              class="btn btn-dark"
              data-bs-toggle="modal"
              data-bs-target="#exampleModal"
              @click="sendInfo(product)"
            >
              Détails
            </button>
          </td>
        </tr>
        <!-- Modal -->
        <div
          class="modal fade "
          id="exampleModal"
          tabindex="-1"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
        >
          <div class="modal-dialog" style="max-width: 70%;" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title styleTitleModal" id="exampleModalLabel">
                  {{ selectedUser.name }}
                </h5>
                <button
                  type="button"
                  class="btn-close"
                  data-bs-dismiss="modal"
                  aria-label="Close"
                ></button>
              </div>
              <div class="styleModal" >
                <img :src="apiImage+selectedUser.media" class="imgProduct"/>
              
                <h3 class="styleTextModal">Catégorie :</h3>
                <p class="styleTextModal">{{ selectedUser.category }}</p >
                <h3 class="styleTextModal">Détails points :</h3>
                <p class="styleTextModal">{{ selectedUser.detailPoints }}</p >
                <h3 class="styleTextModal">Détails :</h3>
                <p class="styleTextModal">{{ selectedUser.details }}</p >
                <h3 class="styleTextModal">Prix :</h3>
                <p class="styleTextModal">{{ selectedUser.price }}</p >
                <br/>
                <input v-model="price_provider" placeholder="Saisie le prix provider">
              </div>
              <div class="modal-footer">
                <button
                  type="button"
                  class="btn btn-secondary"
                  data-bs-dismiss="modal"
                >
                  Close
                </button>
                <button type="button" @click="updatePriceProvider(selectedUser.id,price_provider)" class="btn btn-primary">
                 Enregistrer
                </button>
              </div>
            </div>
          </div>
        </div>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      apiImage : "http://37.187.244.116:5000/static/",
      products: [],
      selectedUser: "",
      price_provider:"",
    };
  },
  mounted() {
    this.getProducts();
  },
  methods: {
    getProducts() {
      axios
        .get(
          "http://37.187.244.116:5000/products/" + this.$route.params.category,
          {
            headers: {
              "Access-Control-Allow-Origin": "*",
              "Content-type": "application/json",
            },
          }
        )
        .then((response) => (this.products = response.data.products));
    },
    sendInfo(item) {
      this.selectedUser = item;
    },
    updatePriceProvider(id,price_provider){
        axios.post("http://37.187.244.116:5000/product/"+id, price_provider,{
           headers: {
              "Access-Control-Allow-Origin": "*",
              "Content-type": "application/json",
            },
        })
    .then(response => console.log('ici',response));
    }
  },
};
</script>
<style scoped>
.tab {
  margin: 25%;
}
.imgProduct{
  width : 60%;
}
.styleTextModal{
 
  width: 100%;
  text-align: left;
  margin-left:5px;
}
.modalsize{
  
  width: 120%;
  margin: auto;

}
.styleTitleModal{
  
  text-align: left;

}
</style>
