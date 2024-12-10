<template>
    <!-- Header -->
    <div class="d-flex justify-content-between">
      <h2>Kártyák</h2>
      <div>
        <div class="dropdown">
          kártya/odal:
          <button
            class="btn btn-outline-secondary dropdown-toggle"
            type="button"
            data-bs-toggle="dropdown"
            aria-expanded="false"
          > asdasd
          </button>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item">Action</a></li>
          </ul>
        </div>
      </div>
    </div>
    <!-- Kártyák -->
    <!-- Ide mennek a kártyák -->

  <!-- Footer -->
   <!-- Ide megy a paginátor -->
</template>

<script>
import axios from 'axios'
export default {
  props:['url'],
  data() {
    return{
      Datas:[],

    }
  },
  mounted(){
    getDatas();
  },
  methods:{
    async getDatas(){
      
    }
  }
}
</script>

<style>

</style>
