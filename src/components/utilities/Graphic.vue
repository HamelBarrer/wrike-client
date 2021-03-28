<template>
  <apexchart
    width="600"
    type="line"
    :options="options"
    :series="series"
  ></apexchart>
</template>

<script>
  import { ref } from '@vue/reactivity';
  import VueApexCharts from 'vue3-apexcharts';
  export default {
    components: { apexchart: VueApexCharts },
    setup() {
      const options = ref({
        chart: {
          id: 'vuechart-example',
        },
        xaxis: {
          categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998],
        },
      });

      const series = ref([
        {
          name: 'series-1',
          data: [30, 40, 45, 50, 49, 60, 70, 91],
        },
      ]);

      return {
        options,
        series,
      };
    },
  };
</script>

<style></style>
