<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>
<script>
export default {
  data(){
    return{
      url: 'http://localhost:8000/api'
    }
  }
}
</script>

<template>
  <nav class="navbar bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
  </div>
</nav>
  <header>

    <div class="">
      <nav>
        <RouterLink to="/">Home</RouterLink> | 
        <RouterLink to="/kartyak">Kártyák</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView
    :url="url"
  />
</template>

<style scoped>

</style>
