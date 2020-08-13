<template>
  <div class="posts-new">
    <h1>{{ message }}</h1>
    <div v-for="post in posts">

      <br>
      <br>
      <b><a v-bind:href="`/posts/${post.id}`">{{post.title}}</a></b>
      <br>
<!-- <div class="card" style="width: 18rem;">
  <img src=https://images-na.ssl-images-amazon.com/images/I/815W5k84jLL._AC_SL1500_.jpg class="card-img-top">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Buy CandyLand and Give Me Money</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div> -->
  
      <br>
      {{post.body}}
      <br>
      <br>
      <i> {{post.image}} </i>
      <p>∞</p>
      </div>
  
  </div>
  </div>
</template>



<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome To Index!",
      posts: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      console.log("Hello");
      axios.get("/api/posts").then((response) => {
        console.log(response);
        this.posts = response.data;
      });
    },
  },
};
</script>