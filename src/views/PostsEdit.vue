<template>
  <div class="posts-edit">
    <div class="container">
      <form v-on:submit.prevent="updatePost()">
        <h1>Edit Post</h1>

        <ul>
          <li v-for="error in errors"> {{error}} </li>
        </ul>

        <div class="form-group">
          <label>Title:</label> 
          <input type="text" class="form-control" v-model="post.title">
        </div>

        <div class="form-group">
          <label>Body: </label>
          <input type="text" class="form-control" v-model="post.body">
        </div>

        <div class="form-group">
          <label>image:</label> 
          <input type="text" class="form-control" v-model="post.image">
        </div>

        <div>
          <input type="submit" class="btn btn-primary" value="Edit post">
        </div>

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
      post: { //see line 56 for why it makes sense to set post as object
        title: "",
        body: "",
        image: "",
      },
      errors: []
    };
  },
  created: function() {
    axios
    .get("/api/posts/" + this.$route.params.id)
    .then(response => {
      this.post = response.data;
    });
  },
  methods: {
    updatePost: function() {
      var clientParams = {
        title: this.post.title,
        body: this.post.body,
        image: this.post.image
      };

      axios
      .patch("/api/posts/" + this.$route.params.id, clientParams)
      .then(response => {
        this.$router.push("/posts/" + this.$route.params.id);
      }).catch(error => {
        this.errors = error.response.data.errors;
      });
    }
  }
};  
</script>