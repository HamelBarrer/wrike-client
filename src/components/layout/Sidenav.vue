<template>
  <aside class="sidenav">
    <ul class="sidenav__item">
      <li class="sidenav__item--list">
        <router-link to="/">Inico</router-link>
      </li>
      <li class="sidenav__item--list">
        <router-link to="/reportes">Reportes</router-link>
      </li>
      <li class="sidenav__item--list">
        <router-link to="/login">Iniciar Sesion</router-link>
      </li>
      <li class="sidenav__item--list">
        <router-link to="/proyectos">Proyectos</router-link>
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
    background-color: #4e4d4d;
    border-left: 5px solid #fff;
  }

  .sidenav__item--list > a {
    color: #fff;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 0.8rem;
  }
</style>
