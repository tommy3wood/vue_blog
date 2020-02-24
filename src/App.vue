<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <a class="navbar-brand" href="#">Butt Talk</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <router-link class="nav-link" to="/"> Home</router-link>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Profile
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdown">
              <router-link class="dropdown-item" to="/signup"> Signup</router-link>
              <router-link class="dropdown-item" to="/login"> Login</router-link>
              <router-link class="dropdown-item" to="/logout"> Logout</router-link>
            </div>   
          </li>
          <li>
            <router-link class="nav-link" to="/posts/new"> Create</router-link>
          </li>
        </ul>
      </div>
    </nav>




    <router-view/>
  </div>

</template>

<style>
  body{
    font-family: Courier New, Courier, Lucida Sans Typewriter, Lucida Typewriter, monospace;
    background-image: url("/bananas.png");
  }

  #container{
    align: center;
  }
</style>
