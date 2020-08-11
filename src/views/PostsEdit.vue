<template>
  <div class="posts-edit">
    <form v-on.submit.prevent="editPost()">
    <h1>{{ message }}</h1>
    <h3> {{post}} </h3>
   

    <div class="form group">
      <label> Title </label>
      <input type="text" class="form-control" v-model="post.title">
    </div> 
    <div class="form group">
      <label> Body </label>
      <input type="text" class="form-control" v-model="post.body">
    </div> 
    <div class="form group">
      <label> Image </label>
      <input type="text" class="form-control" v-model="post.image">
    </div> 
    <input type="submit" class="btn btn-primary" value="Submit">
    </form>
    
    </div>
  </div>
</template>

// want to call a wild card, 
// call it's information
// set that as the default text
// display it as editable

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Edit A Post!",
      post: {},
      errors: [],
    };
  },
  methods: {
    editPost: function () {
      var params = {
        title: this.post.title,
        body: this.post.body,
        image: this.post.image,
      };

      console.log("Edit");

      axios
        .patch(`/api/posts/${this.$route.params.id}`, params)
        .then((response) => {
          this.$router.push("/posts");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
    showPost: function () {
      console.log("Hello");
      console.log(this.$route);
      axios.get(`/api/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.post = response.data;
      });
    },
    created: function () {
      this.showPost();
    },
  },
};
</script>