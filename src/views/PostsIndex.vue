<template>
  <div class="containter">
    <div class="posts-index">
      <h1>Butt Talk</h1>
      <div v-for="post in posts">
        <img v-bind:src="post.image" v-bind:alt="post.title">
        <h2>{{post.title}}</h2>
        <p>{{post.body}}</p>
      </div>
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
      posts: []
    };
  },
  created: function() {
    axios
    .get("/api/posts")
    .then(response => {
      this.posts = response.data;
    });
  },
  methods: {}
};
</script>