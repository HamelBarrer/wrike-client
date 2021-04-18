<template>
  <h2>login</h2>
  <form method="POST" @submit.prevent="sendData" autocomplete="off">
    <input
      type="text"
      placeholder="Nombre de Usuario"
      v-model.trim="username"
    />
    <input
      type="password"
      placeholder="Contraseña de Usuario"
      v-model.trim="password"
    />
    <button type="submit">enviar</button>
  </form>
</template>

<script>
  import { ref } from '@vue/reactivity';
  import { watchEffect } from '@vue/runtime-core';
  export default {
    setup() {
      const username = ref('');
      const password = ref('');

      const token = ref('');

      const sendData = () => {
        fetch(`https://wrikke.herokuapp.com/auth-token/`, {
          method: 'POST',
          body: JSON.stringify({
            username: username.value,
            password: password.value,
          }),
          headers: {
            'Content-Type': 'application/json',
          },
        })
          .then((res) => res.json())
          .catch((error) => console.error('Error:', error))
          .then((response) => {
            console.log(response.t);
            token.value = response.token;
          });
      };

      if (localStorage.getItem('token')) {
        token.value = localStorage.getItem('token');
      }

      watchEffect(() => {
        localStorage.setItem('token', token.value);
      });

      return {
        username,
        password,
        sendData,
      };
    },
  };
</script>

<style></style>
