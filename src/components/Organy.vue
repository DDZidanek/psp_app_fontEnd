<template>
  <div class="container-fluid mt-5">
    <h1>Seznam Orgánů</h1>
    <table id="example3" class="table table-striped" style="width:100%">
      <thead class="thead-dark">
      <tr>
        <th>ID</th>
        <th>Parent ID</th>
        <th>Typ Organu</th>
        <th>Zkratka</th>
        <th>Název CZ</th>
        <th>Název EN</th>
        <th>Od</th>
        <th>Do</th>
        <th>Priorita</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="organ in organy" :key="organ.idOrgan">
        <td>{{ organ.idOrgan }}</td>
        <td>{{ organ.parentOrgan }}</td>
        <td>{{ organ.idTypOrganu }}</td>
        <td>{{ organ.zkratka }}</td>
        <td>{{ organ.nazevOrganuCz }}</td>
        <td>{{ organ.nazevOrganuEn }}</td>
        <td>{{ organ.odOrgan }}</td>
        <td>{{ organ.doOrgan }}</td>
        <td>{{ organ.priorita }}</td>
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
      organy: []
    };
  },
  methods: {
    fetchOrgany() {
      axios.get('http://127.0.0.1:8080/organy')
          .then(response => {
            this.organy = response.data;
            this.$nextTick(() => {
              $('#example3').DataTable();
            });
          })
          .catch(error => {
            console.error('Error fetching data:', error);
          });
    }
  },
  mounted() {
    this.fetchOrgany();
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
