<template>
  <div class="main-card">
    <div class="card">
      <graphic />
    </div>
    <div class="card">d</div>
    <div class="card">d</div>
  </div>
</template>

<script>
  import Graphic from '../components/utilities/Graphic.vue';
  export default {
    components: { Graphic },
  };
</script>

<style scoped>
  .main-card {
    margin-top: 1rem;
    display: grid;
    gap: 1rem;
    grid-template-columns: repeat(3, 1fr);
  }

  .card:nth-child(1) {
    grid-column: 2 span;
  }
</style>
