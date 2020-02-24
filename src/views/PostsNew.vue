<template>
  <div class="posts-new">
    <div class="container">
      <form v-on:submit.prevent="createPost()">
        <h1>New Post</h1>
        <ul>
          <li v-for="error in errors"> {{error}} </li>
        </ul>
        <div class="form-group">
          <label>Title:</label>
          <input type="text" class="form-control" v-model="name">
        </div>
        <div class="form-group">
          <label>Body:</label>
          <input type="text" class="form-control" v-model="body">
        </div>
        <div class="form-group">
          <label>Image:</label>
          <input type="text" class="form-control" v-model="image">
        </div>


        <input type="submit" class="btn btn-primary" value="Flippin Flappin post your keyboard tappin">
      </form>
    </div>
  </div>
</template>


<style>
  
</style>


<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      title: "",
      body: "",
      image: "",
      errors: []
    };
  },
  created: function() {},
  methods: {
    createPost: function() {
      var clientParams = {
        title: this.title,
        body: this.body,
        image: this.image
      };

      axios
      .post("/api/posts", clientParams)
      .then(response => {
        this.$router.push("/posts");
      }).catch(error => {
        this.errors = error.response.data.errors;
      });
    }
  }
};  
</script>