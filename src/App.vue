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
  import Navbar from './components/layout/Navbar.vue';
  import Sidenav from './components/layout/Sidenav.vue';
  export default {
    components: { Navbar, Sidenav },
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
    background-color: #f1eee1;
  }
</style>
