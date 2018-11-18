<template>
  <div class = "home">
    <div class="header_image">
      <img src="http://musicwhore.org/wp-content/uploads/2014/08/20131111_142254.jpg" class="img-fluid" alt="Responsive image">
    </div>

    <div class="container">
      <div class="row mb-4 mt-4">
        <div v-for="product in products" class="col-4 mt-4 mb-4 ">
          <div class="card" style="width: 18rem;">
            <img class="card-img-top" v-bind:src="product.images[0]" alt="Card image cap">
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
  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");

export default {
  data : function() {
    return {
      message: "Welcome to Vue.js!",
      products: []
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
  methods: {},
  computed: {}
};
</script> 