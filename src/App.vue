<template>
  <div id="app">
    <div class="pos-f-t">
        <div class="collapse" id="navbarToggleExternalContent">
          <div class="bg-dark p-4">
              <a href="/#/"> ALL RECORDS</a><br>
              <a href="">ADD YOUR RECORDS</a><br>
              <a href="/#/signup">SIGNUP</a><br>
              <a href="/#/login">LOGIN</a><br>
              <a href="/#/">LOGOUT</a>
            <span class="text-muted"></span>
          </div>
        </div>
        <nav class="navbar navbar-dark bg-dark">
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarToggleExternalContent" aria-controls="navbarToggleExternalContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
        </nav>  
      </div>
    <router-view/>
  </div>
</template>

<style>
</style>
