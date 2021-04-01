<template>
  <form-report />
  <list-report />
  <h2>tablas</h2>
  <carrousel-report />
</template>

<script>
  import { ref } from '@vue/reactivity';
  import FormReport from '../components/report/FormReport.vue';
  import ListReport from '../components/report/ListReport.vue';
  import { provide } from '@vue/runtime-core';
  import CarrouselReport from '../components/report/CarrouselReport.vue';
  export default {
    components: { FormReport, ListReport, CarrouselReport },
    setup() {
      const reports = ref([]);

      fetch(`http://localhost:8000/api/v1/list_report`, {
        headers: {
          Authorization: 'Token e9f52054cd3d9cca3d8cc60115acfdd7934c663a',
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

<style></style>
