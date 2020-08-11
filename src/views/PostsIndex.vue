<template>
  <div class="posts-new">
    <h1>{{ message }}</h1>
    <div v-for="post in posts">
      <br>
      <br>
      <b><a v-bind:href="`/posts/${post.id}`">{{post.title}}</a></b>
      <br>
      <br>
      {{post.body}}
      <br>
      <br>
      <i> {{post.image}} </i>
      <p>∞</p>
      </div
  
  </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome To Index!",
      posts: []
    };
  },
  created: function() {
    this.indexProducts();
  },
  methods: {
    indexProducts: function() {
      console.log("Hello");
      axios.get("/api/posts").then(response => {
        console.log(response);
        this.posts = response.data;
      });
    }
  }
};
</script>