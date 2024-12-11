<template>
  <div>
    <!-- Header -->
    <div class="d-flex justify-content-between">
      <h2>Kártyák</h2>
      <div>
        <div class="dropdown">
          kártya/odal:
          <select
            class="form-select"
            aria-label="Default select example"
            v-model="rowsPerPage"
          >
            <option
              v-for="rowsnumber of rowsPerPageArray"
              :key="rowsnumber"
              :value="rowsnumber"
            >
              {{ rowsnumber }}
            </option>
          </select>
        </div>
      </div>
    </div>
    <!-- Kártyák -->
    <div>
      <Cards :datas="datas" />
    </div>

    <!-- Footer -->
    <!-- Ide megy a paginátor -->
    <div>
      <h4>Paginátor</h4>
    </div> 
  </div>
</template>

<script>
import Cards from "@/components/Cards.vue";
import axios from "axios";
export default {
  components: {Cards},
  props: ["url"],
  data() {
    return {
      datas: [],
      rowsPerPage: 5,
      pageNumber: 1,
      numberOfPages: 1,
      rowsPerPageArray: [1, 3, 5, 10, 25, 50, 100],
    };
  },
  watch: {
    rowsPerPage() {
      this.getDatas();
    },
  },
  mounted() {
    this.getDatas();
    
  },
  methods: {
    async getDatas() {
      const url = `${this.url}/queryOsztalynevsorLimit/${this.pageNumber}/${this.rowsPerPage}`;
      const response = await axios.get(url);
      this.datas = response.data.data;
      console.log(this.datas);
    },
  },
};
</script>

<style></style>
