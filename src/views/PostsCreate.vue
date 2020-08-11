<template>
  <div class="posts-create">
    
    <h1>{{ message }}</h1>
      Title:  <input v-model="title" type:text></input>
      <br>
      Body:  <input v-model="body" type:text> </input>
      <br>
      Image URL:<input v-model="image" type:text>  </input>
      <br>
      <button v-on:click="createPost()">Create</button>
        <br>
        <br>
        <b> </b>
        <br>
        <br>
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
  data: function() {
    return {
      message: "Create A Post!",
      posts: [],
      title: "",
      body: "",
      image: "",
      user_id: "",
      errors: []
    };
  },
  created: function() {},
  methods: {
    createPost: function() {
      var params = {
        title: this.title,
        body: this.body,
        image: this.image
      };
      console.log("Hello");
      axios
        .post("/api/posts/new", params)
        .then(response => {
          console.log(response).data;
          this.posts.push(response.data);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>