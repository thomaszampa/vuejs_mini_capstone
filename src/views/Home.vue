<template>
  <div class="home">
    <div class="header_image">
      <img
        src="http://musicwhore.org/wp-content/uploads/2014/08/20131111_142254.jpg"
        class="img-fluid"
        alt="Responsive image"
      />
    </div>

    <div class="container">
      <div class="row mb-4 mt-4">
        <div v-for="product in products" class="col-4 mt-4 mb-4 ">
          <div class="card" style="width: 18rem;">
            <img
              class="card-img-top"
              v-bind:src="product.images[0]"
              alt="Card image cap"
            />
            <div class="card-body">
              <h3 class="card-title">{{ product.name }}</h3>
              <p class="card-price">$ {{ product.price }}</p>
              <p class="card-text">{{ product.description }}</p>
              <a href="#" class="btn btn-primary">Add To Cart</a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <h1>ADD YOUR RECORD HERE</h1>
    Name: <input v-model="newProductName" name="text" /> Price:
    <input v-model="newProductPrice" name="decimal" /> Description:
    <input v-model="newProductDescription" name="text" /> Supplier ID:
    <input v-model="newProductSupplierId" name="integer" />
      <div>
       <button v-on:click="createProduct();" class="btn btn-primary">Create</button>
      </div>
      <div>
        <ul>
          <li v-for="error in errors" class="text-danger">{{error}}</li>
        </ul>
      </div>
  </div>
</template>

<style></style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      products: [],
      newProductName: "",
      newProductPrice: "",
      newProductDescription: "",
      newProductSupplierId: "",
      errors: []
    };
  },
  created: function() {
    axios.get("http://localhost:3000/api/products").then(
      function(response) {
        console.log(response.data);
        this.products = response.data;
      }.bind(this)
    );
  },
  methods: {
    createProduct() {
      console.log("createProduct");
      this.errors = [];
      var params = {
        name: this.newProductName,
        price: this.newProductPrice,
        description: this.newProductDescription,
        supplier_id: this.newProductSupplierId,
      };
      axios
        .post("http://localhost:3000/api/products", params)
        .then(
          function(response) {
            console.log(response);
            this.product.push(response.data);
            this.newProductName = "";
            this.newProductPrice = "";
            this.newProductDescription = "";
            this.newProductSupplierId = "";
          }.bind(this)
        )
        .catch(
          function(error) {
            console.log(error.response.data.errors);
            this.errors = error.response.data.errors;
          }.bind(this)
        );
    }
  },
  computed: {}
};
</script>
