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
    </form>
  </div>
</template>

<script>
  import { ref } from '@vue/reactivity';
  export default {
    setup() {
      const title = ref('');
      const matter = ref('');
      const description = ref('');

      const createReport = () => {
        console.log('casi');
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
