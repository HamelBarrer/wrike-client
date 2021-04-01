<template>
  <div class="corrousel">
    <div class="corrousel__title">
      <h3>Reportes asignados</h3>
    </div>
    <div class="corrousel__header">
      <div class="report" v-for="report in reports" :key="report.id">
        <div class="report__title">
          <h3 class="report__title--title">{{ report.title }}</h3>
          <span class="report__title--createat">{{ report.created_at }}</span>
        </div>
        <div class="report__content">
          <div class="report__content--matter">{{ report.matter }}</div>
          <div class="report__content--description">
            {{ report.description }}
          </div>
        </div>
        <div class="report__footer">
          <div class="report__footer--user">
            {{ report.user }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { inject } from '@vue/runtime-core';
  export default {
    setup() {
      const reports = inject('reports');

      return {
        reports,
      };
    },
  };
</script>

<style></style>
