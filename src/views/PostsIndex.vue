<template>
  <div class="posts-index">
    <br>
    <div class="containter">
      <div v-for="post in posts">
        <div class="card mb-3" style="max-width: 50%;">
          <div class="row no-gutters">
            <div class="col-md-4">
              <img v-bind:src="post.image" class="card-img" v-bind:alt="post.title">
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <router-link v-bind:to="'/posts/' + post.id">
                  <h5 class="card-title">{{post.title}}</h5>
                </router-link>
                <p class="card-text">{{post.body}}</p>
              </div>
            </div>
          </div>
        </div>
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