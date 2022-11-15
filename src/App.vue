<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light" style="padding: 0.5rem 1rem;">
  <div class="navbar-brand">Test App</div>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <a class="nav-link" href="/">Products</a>
      </li>
    </ul>
  </div>
</nav>

  <RouterView />
</template>

