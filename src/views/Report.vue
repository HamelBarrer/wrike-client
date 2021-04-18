<template>
  <h2 class="title">Crear Reporte</h2>
  <form-report />
  <carrousel-report />
</template>

<script>
  import { ref } from '@vue/reactivity';
  import FormReport from '../components/report/FormReport.vue';
  import { provide } from '@vue/runtime-core';
  import CarrouselReport from '../components/report/CarrouselReport.vue';
  export default {
    components: { FormReport, CarrouselReport },
    setup() {
      const reports = ref([]);

      fetch(`https://wrikke.herokuapp.com/api/v1/list_report`, {
        headers: {
          Authorization: `Token ${localStorage.getItem('token')}`,
        },
      })
        .then((response) => response.json())
        .then((data) => {
          reports.value = data;
        });

      provide('reports', reports);
    },
  };
</script>

<style scoped>
  .title {
    text-align: center;
    margin-top: 1rem;
    text-transform: uppercase;
    font-weight: bold;
    color: #5d6163f2;
  }
</style>
