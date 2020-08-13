<template>
  <div class="post-show">
    <h1>{{ message }}</h1>
      <br>
      <br>
      <b>{{post.title}}</b>
      <br>
      <br>
      {{post.body}}
      <br>
      <br>
      <img v-bind:src="post.image">
      <br>
      <button v-on:click="deletePost()"> Delete This Post </button>
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
  data: function () {
    return {
      message: "Showing One Post!",
      post: [],
    };
  },
  created: function () {
    this.showPosts();
  },
  methods: {
    showPosts: function () {
      console.log("Hello");
      console.log(this.$route);
      axios.get(`/api/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.post = response.data;
      });
    },
    deletePost: function () {
      console.log("Hi!");
      axios.delete(`api/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.$router.push("/posts");
      });
    },
  },
};
</script>