<template>
  <div class="form-data">
    <form v-on:submit.prevent="createReport" autocomplete="off" class="form">
      <div class="form__elemt">
        <label for="">Titulo:</label>
        <input type="text" v-model.trim="title" />
      </div>
      <div class="form__elemt">
        <label for="">Asunto:</label>
        <input type="text" v-model.trim="matter" />
      </div>
      <div class="form__elemt">
        <label for="">Descripcion:</label>
        <textarea v-model.trim="description"></textarea>
      </div>
      <button type="submit">Enviar</button>
    </form>
  </div>
</template>

<script>
  import { ref } from '@vue/reactivity';
  import { inject } from '@vue/runtime-core';
  export default {
    setup() {
      const title = ref('');
      const matter = ref('');
      const description = ref('');
      const reports = inject('reports');

      const createReport = () => {
        if (
          title.value === '' ||
          matter.value === '' ||
          description.value === ''
        ) {
          console.log('datos incompletos');
          return;
        }

        fetch(`http://localhost:8000/api/v1/create_report`, {
          method: 'POST',
          body: JSON.stringify({
            title: title.value,
            matter: matter.value,
            description: description.value,
          }),
          headers: {
            Authorization: `Token ${localStorage.getItem('token')}`,
            'Content-Type': 'application/json',
          },
        })
          .then((res) => res.json())
          .catch((error) => console.log(error))
          .then((response) => {
            reports.value.push(response);
          });
      };

      return {
        title,
        matter,
        description,
        createReport,
      };
    },
  };
</script>

<style scoped>
  .form-data {
    margin-top: 2rem;
    background-color: #fff;
    padding: 1rem;
    box-shadow: 1px 1px 6px 1px red;
  }

  .form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
</style>
