<template>
  <div class="form-data">
    <form v-on:submit.prevent="createReport" autocomplete="off" class="form">
      <div class="form__elemt">
        <input
          class="form__elemt-input"
          type="text"
          placeholder="Titulo del reporte"
          v-model.trim="title"
        />
      </div>
      <div class="form__elemt">
        <input
          class="form__elemt-input"
          type="text"
          placeholder="Asunto del reporte"
          v-model.trim="matter"
        />
      </div>
      <div class="form__elemt">
        <textarea
          class="form__elemt-input"
          placeholder="Descripcion del reporte"
          v-model.trim="description"
        ></textarea>
      </div>
      <button class="form__send" type="submit">Enviar</button>
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
    margin: 2rem auto;
    background-color: #fff;
    padding: 1rem;
    width: 50%;
    border-radius: 1rem;
    box-shadow: 1px 1px 6px 1px #8e9aa5;
  }

  .form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .form__elemt {
    padding: 0.5rem 0;
  }

  .form__elemt-input {
    width: 100%;
    padding: 0.5rem;
    border: 0.15rem solid #909ba5;
    border-radius: 1rem;
    outline: none;
    color: #5c5656;
    text-align: center;
  }

  .form__elemt-input::placeholder {
    color: #000;
  }

  .form__send {
    padding: 0.5rem;
    background-color: rgb(114, 165, 114);
    color: #fff;
    text-transform: uppercase;
    font-weight: bold;
    outline: none;
    border: none;
    border-radius: 1rem;
  }
</style>
