<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>
<script>
export default {
  data() {
    return {
      url: "http://localhost:8000/api",
    };
  },
};
</script>

<template>
  <div>

    <h1>Iskola</h1>
    <header>
      <nav class="m-3">
        <RouterLink to="/">Home</RouterLink> |
        <RouterLink to="/kartyak">Kártyák</RouterLink>
        <RouterLink to="/betores">Betörés</RouterLink>
      </nav>
    </header>
    
    <RouterView :url="url" />
  </div>
</template>

<style scoped></style>
