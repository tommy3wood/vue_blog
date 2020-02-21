<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/signup">Signup</router-link> |
      <router-link to="/login">Login</router-link> |
      <router-link to="/logout">Logout</router-link> |
      <router-link to="/posts">Posts</router-link> |
      <router-link to="/posts/new">Create</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
  
</style>
