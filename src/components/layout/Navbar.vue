<template>
  <header class="header">
    <div class="header__logo">
      <h2>Wrike</h2>
    </div>
    <nav class="header__menu">
      <ul class="header__menu--item">
        <li class="header__item--list">
          <router-link to="/">Inicio</router-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
  export default {};
</script>

<style scoped>
  .header {
    grid-area: header;
    display: flex;
    position: fixed;
    width: 100%;
    height: 3rem;
    align-items: center;
    justify-content: space-between;
    padding: 1.5rem;
    background-color: #fff;
  }

  .header__logo {
    font-weight: bold;
    text-transform: uppercase;
    font-size: 0.8rem;
  }
</style>
