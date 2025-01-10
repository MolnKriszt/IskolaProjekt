<template>
  <div>
    <h1>Diákok</h1>
    <table class="table table-striped-columns table-hover">
      <thead>
        <tr class="text-center">
          <th></th>
          <th>Név</th>
          <th>Osztály</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(student, index) in students" :key="index">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ student.nev }}</td>
          <td>{{ student.osztalyNev }}</td>
          <td class="text-center"><button class="btn btn-primary">Button</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { BASE_URL } from "../helpers/baseUrls";
import axios from "axios";

export default {
  data() {
    return {
      urlApi: BASE_URL,
      students: [],
    };
  },
  async mounted() {
    await this.getStudents();
  },
  methods: {
    async getStudents() {
      try {
        const url = `${this.urlApi}/queryOsztalynevsorokosszes`;
        const response = await axios.get(url);
        this.students = response.data.data; 
        console.log(this.students);
      } catch (error) {
        console.error("Hiba történt az adatok lekérése közben:", error);
      }
    },
  },
};
</script>

<style>

</style>
