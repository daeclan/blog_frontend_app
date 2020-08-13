<template>
  <div class="posts-create">
    <img v-if="status" v-bind:src="`https://http.cat/${status}`">
    <h1>{{ message }}</h1>

      <div class="form-group">
        <label>Title:</label>
        <input v-model="title" type:text></input>
        <br>
         <small v-if="title.length <= 20">You have {{ 20 - title.length }} characters remaining</small>
         <small v-if="title.length > 20">Your username is too long, has to be a max of 20 characters</small>
      
      </div>
    
      Body:  <input type="text" v-model="body" class="red-sometimes"> </input>
      <br>
       <small v-if="body.length > 0">{{280 - body.length}}</small>
       <small v-if="body.length > 280">Your Body Is Too Big</small>
       <small v-if="body.length > 280">Your Body Is Too Big</small>
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
  data: function () {
    return {
      message: "Create A Post!",
      posts: [],
      title: "",
      body: "",
      image: "",
      user_id: "",
      errors: [],
      status: "",
    };
  },
  created: function () {},
  methods: {
    createPost: function () {
      var params = {
        title: this.title,
        body: this.body,
        image: this.image,
      };
      console.log("Hello");
      axios
        .post("/api/posts/new", params)
        .then((response) => {
          console.log(response).data;
          this.posts.push(response.data);
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
          console.log(error.response);
          this.status = error.response.status;
        });
    },
  },
};
</script>