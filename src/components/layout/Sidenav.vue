<template>
  <aside class="sidenav">
    <ul class="sidenav__item">
      <li class="sidenav__item--list">
        <router-link to="/">Inico</router-link>
      </li>
      <li class="sidenav__item--list">
        <router-link to="/">Reportes</router-link>
      </li>
    </ul>
  </aside>
</template>

<script>
  export default {};
</script>

<style scoped>
  .sidenav {
    grid-area: sidenav;
    background-color: #303030;
    position: fixed;
    width: 12rem;
    height: 100%;
    margin-top: 3rem;
  }

  .sidenav__item {
    display: flex;
    flex-direction: column;
  }

  .sidenav__item--list {
    padding: 1rem 1rem 1rem 1rem;
    align-items: center;
  }

  .sidenav__item--list:hover {
    background-color: white;
    border-left: 5px solid red;
  }

  .sidenav__item--list > a {
    color: #fff;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 0.8rem;
  }
</style>
