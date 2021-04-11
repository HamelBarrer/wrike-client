<template>
  <div class="main-content">
    <navbar />
    <sidenav />
    <main class="main">
      <div class="container">
        <router-view />
      </div>
    </main>
  </div>
</template>

<script>
  import { ref } from '@vue/reactivity';
  import Navbar from './components/layout/Navbar.vue';
  import Sidenav from './components/layout/Sidenav.vue';
  import { provide } from '@vue/runtime-core';
  export default {
    components: { Navbar, Sidenav },
    setup() {
      const reports = ref([]);

      provide('reports', reports);
    },
  };
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    text-rendering: optimizeLegibility;
    font-family: Arial, Helvetica, sans-serif;
  }

  a {
    text-decoration: none;
  }

  li {
    list-style: none;
  }

  .container {
    width: 90%;
    margin: auto;
  }

  .card {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
    justify-content: center;
    background-color: #fff;
    padding: 1rem;
    box-shadow: 0 32px 32px -10px rgb(112 105 103 / 9%),
      0 16px 16px -10px rgb(112 105 103 / 7%),
      0 8px 8px -10px rgb(112 105 103 / 4%),
      0 4px 4px -10px rgb(112 105 103 / 2%),
      0 2px 4px -10px rgb(112 105 103 / 1%);
    border-radius: 1rem;
  }

  .main-content {
    display: grid;
    grid-template-areas:
      'header header'
      'sidenav main'
      'sidenav main';
    grid-template-rows: 3rem 1fr 2rem;
    grid-template-columns: 12rem 1fr;
    height: 100%;
  }

  .main {
    grid-area: main;
    background-color: #fafaf8;
  }
</style>
