<template>
  <nav aria-label="Page navigation example">
    <ul class="pagination justify-content-center">
      <!-- Previous gomb -->
      <li class="page-item">
        <a
          class="page-link"
          @click="Prev()"
          :class="{ disabled: currentPage === 1 }"
        >
          Previous
        </a>
      </li>

      <!-- Oldalszámok -->
      <li class="page-item" v-for="page in totalPages" :key="page">
        <a
          class="page-link"
          @click="goToPage(page)"
          :class="{ active: currentPage === page }"
        >
          {{ page }}
        </a>
      </li>

      <!-- Next gomb -->
      <li class="page-item">
        <a
          class="page-link"
          @click="Next()"
          :class="{ disabled: currentPage === totalPages }"
        >
          Next
        </a>
      </li>
    </ul>
    <!-- <p>
      currentPage: {{ currentPage }} | 
      totalPages: {{ totalPages }}

    </p> -->
  </nav>
</template>

<script>
export default {
  props: {
    currentPage: Number,
    totalPages: Number,
  },
  methods: {
    goToPage(page) {
      this.$emit("page-changed", page); 
    },

    Prev() {
      if (this.currentPage > 1) {
        this.$emit("page-changed", this.currentPage - 1); 
      }
    },

    Next() {
      if (this.currentPage < this.totalPages) {
        this.$emit("page-changed", this.currentPage + 1);  
      }
    },
  },
};
</script>

<style scoped>

</style>
