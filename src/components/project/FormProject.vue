<template>
  <div class="form-data">
    <form v-on:submit.prevent="createReport" autocomplete="off" class="form">
      <div class="form__elemt">
        <select multiple class="form__elemt-input" v-model="developer">
          <option
            v-for="develop in developers"
            :key="develop.id"
            v-bind:value="develop.username"
          >
            {{ develop.username }}
          </option>
        </select>
      </div>
      <div class="form__elemt">
        <input
          class="form__elemt-input"
          type="text"
          placeholder="Titulo del reporte"
          v-model.trim="title"
        />
      </div>
      <div class="form__elemt">
        <textarea
          class="form__elemt-input"
          placeholder="Descripcion del reporte"
          v-model.trim="description"
        ></textarea>
      </div>
      <div class="form__elemt">
        <input
          class="form__elemt-input"
          type="date"
          placeholder="Asunto del reporte"
          v-model.trim="start_date"
        />
      </div>
      <div class="form__elemt">
        <input
          class="form__elemt-input"
          type="date"
          placeholder="Asunto del reporte"
          v-model.trim="end_date"
        />
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
      const developer = ref([]);
      const title = ref('');
      const description = ref('');
      const start_date = ref('');
      const end_date = ref('');
      const reports = inject('reports');
      const developers = ref([]);

      fetch(`http://localhost:8000/api/v1/list_user`, {
        method: 'GET',
        headers: {
          Authorization: `Token ${localStorage.getItem('token')}`,
          'Content-Type': 'application/json',
        },
      })
        .then((response) => response.json())
        .catch((error) => console.log(error))
        .then((response) => {
          developers.value = response;
        });

      const createReport = () => {
        if (
          title.value === '' ||
          start_date.value === '' ||
          description.value === ''
        ) {
          console.log('datos incompletos');
          return;
        }

        fetch(`http://localhost:8000/api/v1/create_project`, {
          method: 'POST',
          body: JSON.stringify({
            developer: developer.value,
            title: title.value,
            description: description.value,
            start_date: start_date.value,
            end_date: end_date.value,
          }),
          headers: {
            Authorization: `Token ${localStorage.getItem('token')}`,
            'Content-Type': 'application/json',
          },
        })
          .then((res) => res.json())
          .catch((error) => console.log('err', error))
          .then((response) => {
            reports.value.push(response);
          });
      };

      return {
        developer,
        title,
        start_date,
        end_date,
        description,
        createReport,
        developers,
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
    background-color: #fff;
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
