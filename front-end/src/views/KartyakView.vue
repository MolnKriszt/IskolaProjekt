<template>
  <div>
    <!-- Header -->
    <div class="d-flex flex-column container-fluid">
      <div class="d-flex justify-content-between mb-3">
        <h2>Kártyák</h2>
        <!-- <p>currentPage: {{ currentPage }} | totalPages: {{ totalPages }}</p> -->
        <div>
          <div class="dropdown d-flex align-items-center">
            <span class="me-2"> kártya/odal: </span>
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
      <div class="my-cards-height overflow-auto my-border">
        <Cards :datas="datas" />
      </div>

      <!-- Footer -->
      <Paginator
        :currentPage="currentPage"
        :totalPages="totalPages"
        @page-changed="handlePageChange"
      />
    </div>
  </div>
</template>

<script>
import Cards from "@/components/Cards.vue";
import Paginator from "@/components/Paginator.vue";
import axios from "axios";

export default {
  components: { Cards, Paginator },
  props: ["url"],
  data() {
    return {
      datas: [],
      rowsPerPage: 5,
      currentPage: 1,
      totalPages: 1,
      rowsPerPageArray: [1, 3, 5, 10, 25, 50, 100],
    };
  },
  watch: {
    async rowsPerPage() {
      await this.getDatas();
      await this.getHowManyPages();
      this.currentPage = Math.min(this.currentPage, this.totalPages);
    },
    async currentPage() {
      await this.getDatas();
    },
  },
  mounted() {
    this.getDatas();
    this.getHowManyPages();
  },
  methods: {
    async getDatas() {
      const url = `${this.url}/queryOsztalynevsorLimit/${this.currentPage}/${this.rowsPerPage}`;
      const response = await axios.get(url);
      this.datas = response.data.data;
      console.log(this.datas);
    },
    async getHowManyPages() {
      const url = `${this.url}/queryHanyOldalVan/${this.rowsPerPage}`;
      const response = await axios.get(url);
      this.totalPages = response.data.data.oldalszam;
    },

    handlePageChange(page) {
      this.currentPage = page;
      this.getDatas();
    },
  },
};
</script>

<style>
.my-cards-height {
  height: calc(100vh - 300px);
}
</style>
