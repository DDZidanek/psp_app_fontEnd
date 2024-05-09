<template>
  <div class="container-fluid mt-5">
    <h1>Seznam Poslanců</h1>
      <table id="example2" class="table table-striped" style="width:100%">
        <thead class="thead-dark">
        <tr>
          <th>ID Poslanec</th>
          <th>Před</th>
          <th>Jméno</th>
          <th>Příjmení</th>
          <th>Za</th>
          <th>Narození</th>
          <th>Pohlaví</th>
          <th>Změna</th>
          <th>Úmrtí</th>
          <th>ID Kraj</th>
          <th>Web</th>
          <th>Email</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="poslanec in poslanci" :key="poslanec.idPoslanec">
          <td>{{ poslanec.idPoslanec }}</td>
          <td>{{ poslanec.idOsoba.pred }}</td>
          <td>{{ poslanec.idOsoba.jmeno }}</td>
          <td>{{ poslanec.idOsoba.prijmeni }}</td>
          <td>{{ poslanec.idOsoba.za }}</td>
          <td>{{ poslanec.idOsoba.narozeni }}</td>
          <td>{{ poslanec.idOsoba.pohlavi }}</td>
          <td>{{ poslanec.idOsoba.zmena }}</td>
          <td>{{ poslanec.idOsoba.umrti }}</td>
          <td>{{ poslanec.idKandidatka }}</td>
          <td>{{ poslanec.web }}</td>
          <td>{{ poslanec.email }}</td>
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
      poslanci: []
    };
  },
  methods: {
    fetchPoslanci() {
      axios.get('http://127.0.0.1:8080/poslanci')
          .then(response => {
            this.poslanci = response.data;
            this.$nextTick(() => {
              $('#example2').DataTable();
            });
          })
          .catch(error => {
            console.error('Error fetching data:', error);
          });
    }
  },
  mounted() {
    this.fetchPoslanci();
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
