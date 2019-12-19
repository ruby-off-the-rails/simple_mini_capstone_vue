<template>
  <div class="products-new">
    <h1>{{ message }}</h1>
    <form v-on:submit.prevent="makeProduct()">
      <p>name: <input type="text" v-model="name"></p>
      <p>description: <input type="text" v-model="description"></p>
      <p>price: <input type="text" v-model="price"></p>
      <p>image_url: <input type="text" v-model="imageUrl"></p>
      <button>Make a new product</button>
    </form>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to the new page, make a new product!",
      imageUrl: "",
      price: "",
      name: "",
      description: ""
    };
  },
  created: function() {},
  methods: {
    makeProduct: function() {
      var params = {
        name: this.name,
        price: this.price,
        description: this.description,
        image_url: this.imageUrl
      };

      console.log(params);
      axios.post("/api/products", params).then(response => {
        console.log(response.data);
      }).catch(errors => {
        console.log(errors.response.data);
      })
      console.log('making the product');
    }
  }
};
</script>
