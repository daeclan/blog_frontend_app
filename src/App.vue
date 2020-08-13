<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/postsindex">Index</router-link> |
      <router-link to="/posts/new">Create Post</router-link> |
      <router-link to="/posts/:id">Show Post</router-link> |
      <router-link to="/posts/:id/edit">Edit Post</router-link> |
      <router-link to="/about">About</router-link> |
      <span v-if="!isLoggedIn()"><router-link to="/signup">Signup </router-link>  </span>
      <span v-if="!isLoggedIn()">| <router-link to="/login">Login</router-link> </span>
      <span v-if="isLoggedIn()"> <router-link to="/logout"> Logout</router-link></span>
    </div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <a class="navbar-brand" href="#">Welcome To Blogsville</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#Index">Index</a>
      </li>
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Dropdown
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <div class="dropdown-divider"></div>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
      </li>
    </ul>
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
    </form>
  </div>
</nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Garamond, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #e0911f;
  /* background: url(https://s3.amazonaws.com/noupe/2009/10/squidfingers.jpg); */
}

#navbar {
  background: #e0911f;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #c71e00;
}

#nav a.router-link-exact-active {
  color: #ffffff;
}

#red-sometimes {
  color: #c71e00;
}
</style>

<script>
export default {
  methods: {
    isLoggedIn: function () {
      console.log("Hello");
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },

    getUserId: function () {
      return localStorage.getItem("user_id");
    },
  },
};
</script>