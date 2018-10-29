<template>
  <div class="home">
    <div class="row">
      <div class="col-md-4" v-for="product in products">
        <h1>{{ product.name }}</h1>
        <h3>{{ product.formatted.price }}</h3>

        <div class="card" style="width: 18rem;">
          <img class="card-img-top" v-bind:src="product.default_image_url" v-bind:alt="product.name">
          <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <p class="card-text">{{ product.description }}</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
</style>

<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      products: [{formatted:{}, images: [{url: "", alt: ""}]}]
    };
  },
  created: function() {
    axios
    .get("/api/products")
    .then(response => {
      console.log(response.data)
      this.products = response.data;
    });
  },
  methods: {},
  computed: {}
};
</script>
