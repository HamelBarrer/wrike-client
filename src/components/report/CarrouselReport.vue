<template>
  <div class="carrousel-content">
    <div class="card" v-for="report in reports" :key="report.id">
      <div class="card__title">
        <h3 class="card__title--title">{{ report.title }}</h3>
        <span class="card__title--createat">{{ report.created_at }}</span>
      </div>
      <div class="card__content">
        <div class="card__content--matter">{{ report.matter }}</div>
        <div class="card__content--description">
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

<style scoped>
  .carrousel-content {
    display: grid;
    gap: 1rem;
    grid-template-columns: repeat(4, 1fr);
  }
</style>
