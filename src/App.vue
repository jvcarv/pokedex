<script setup></script>
<template>
  <nav class="navbar navbar-expand-lg bg-danger">
    <div class="container-fluid"> 
      <router-link class="navbar-brand" to="/">
        <img src="https://cdn-icons-png.flaticon.com/512/188/188987.png" alt="Bootstrap" width="70" height="56">
        Pokédex
      </router-link> 
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation"> <span class="navbar-toggler-icon"></span> </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav"> 
            <router-link class="nav-link" aria-current="page" to="/">Home</router-link> 
            <router-link class="nav-link" to="/about">About</router-link> 
          </div>
        </div>
    </div>
  </nav>

  <!--CONTENT-->
  <div class="main">
    <router-view></router-view>
  </div>


  <footer class="bg-danger">
    <div>
     Design in {{new Date().getFullYear()}}
    </div>
  </footer>
</template>


<style>
  footer{
    position: fixed;
    bottom: 0;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 56px;
  }

  body{
    height: 100vh;
    background: rgb(2,0,36);
    background: linear-gradient(0deg, rgba(2,0,36,0.9108018207282913) 8%, rgba(104,213,215,0.8827906162464986) 65%, rgba(64,0,255,0.41780462184873945) 94%);
  }

</style>