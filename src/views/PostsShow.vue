<template>
  <div class="posts-show">
    <div class="container">

      <div class="card mb-3">
        <img v-bind:src="post.image" class="card-img-top" v-bind:alt="post.title">
        <div class="card-body">
          <h5 class="card-title">{{post.title}}</h5>
          <p class="card-text">{{post.body}}</p>
        </div>
        <router-link v-bind:to="'/posts/' + post.id + '/edit'">
          <input type="submit" class="btn btn-primary" value="Edit">
        </router-link>
        <div>
            <input v-on:click="destroyPost" type="submit" class="btn btn-danger" value="DELETE">
          </router-link>
        </div>
      </div>

    </div>
  </div> 
</template>

<style>
</style>

<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      post: {
        title: "",
        body: "",
        image: "",
      }
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
    destroyPost: function() {
      axios
      .delete("/api/posts/" + this.$route.params.id)
      .then(response => {
        this.$router.push("/");
      });
    }
  }
};
</script>