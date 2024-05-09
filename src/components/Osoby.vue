<template>
  <div class="container-fluid mt-5">
    <h1>Seznam osob</h1>
    <table id="example" class="table table-striped" style="width:100%">
      <thead class="thead-dark">
      <tr>
        <th>ID</th>
        <th>Před</th>
        <th>Jméno</th>
        <th>Příjmení</th>
        <th>Za</th>
        <th>Narození</th>
        <th>Pohlaví</th>
        <th>Změna</th>
        <th>Úmrtí</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="osoba in osoby" :key="osoba.idOsoba">
        <td>{{ osoba.idOsoba }}</td>
        <td>{{ osoba.pred }}</td>
        <td>{{ osoba.jmeno }}</td>
        <td>{{ osoba.prijmeni }}</td>
        <td>{{ osoba.za }}</td>
        <td>{{ osoba.narozeni }}</td>
        <td>{{ osoba.pohlavi }}</td>
        <td>{{ osoba.zmena }}</td>
        <td>{{ osoba.umrti }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
import $ from 'jquery';
import 'datatables.net-bs5';
import 'datatables.net-responsive-bs5'
import 'bootstrap';
import 'bootstrap/dist/css/bootstrap.min.css';

export default {
  data() {
    return {
      osoby: []
    };
  },
  methods: {
    fetchOsoby() {
      axios.get('http://127.0.0.1:8080/osoby')
          .then(response => {
            this.osoby = response.data;
            this.$nextTick(() => {
              $('#example').DataTable();
            });
          })
          .catch(error => {
            console.error('Error fetching data:', error);
          });
    }
  },
  mounted() {
    this.fetchOsoby();
  }
}
</script>



<style scoped>
.container-fluid {
  padding: 20px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  background-color: white;
  border-radius: 5px;
  width: 100%;
  max-width: none;
}

table {
  width: 100%;
}

.dataTables_wrapper {
  width: 100%;
}

thead {
  background-color: #343a40;
  color: white;
}

.dataTables_wrapper .dataTables_filter {
  float: right;
}

.dataTables_wrapper .dataTables_length {
  float: left;
}

.dataTables_wrapper .dataTables_paginate {
  float: right;
}

.dataTables_wrapper .dataTables_info {
  clear: both;
  padding-top: 0.5em;
}
td
{
  width: 100px;
}
</style>
