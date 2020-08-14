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
      <p>post.user_id {{post.user_id}}
      <p>current user's id {{ $parent.getUserId()}}
      <br>
        <span v-if="post.user_id == $parent.getUserId()">
          <br>
          <a v-bind:href="`/posts/${post.id}/edit`">Edit This Post</a>
          <br>
          <button v-on:click="deletePost()"> Delete This Post </button>
        </span>
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