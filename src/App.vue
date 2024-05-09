<template>
  <head>
    <meta charset="UTF-8">
    <link rel="icon" href="/favicon.ico">
    <title>Vite App</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdn.datatables.net/1.12.1/css/dataTables.bootstrap5.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.datatables.net/responsive/2.3.0/css/responsive.bootstrap4.min.css">
  </head>
  <div>
    <header class="bg-light p-3 mb-4 border-bottom">
      <h1>PSP Data</h1>
    </header>

    <Osoby />
    <Poslanci />
    <Organy />
    <footer class="footer bg-light p-3 border-top" style="margin-top: 50px;">
      <p class="text-center m-0">© 2024 PSP Data</p>
    </footer>
  </div>
</template>

<script>
import Osoby from './components/Osoby.vue';
import Organy from "@/components/Organy.vue";
import Poslanci from "@/components/Poslanci.vue";

export default {
  name: 'App',
  components: {
    Osoby,
    Organy,
    Poslanci
  }
}
</script>

<style>
</style>
