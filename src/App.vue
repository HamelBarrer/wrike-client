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
    width: 100%;
    align-items: center;
    justify-content: center;
    background-color: #fff;
    padding: 1rem;
    box-shadow: 0 4px 4px 3px rgba(75, 102, 171, 0.2);
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
    height: 100vh;
  }

  .main {
    grid-area: main;
    background-color: #f9fbfd;
  }
</style>
