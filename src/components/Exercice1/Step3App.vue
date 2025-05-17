<!-- components/StepThree.vue -->
<template>
    <div>
      <h2>Étape 3 : Spécifications de l'enfant</h2>
      <form @submit.prevent="submitForm">
        <label>
          Classe:
          <select v-model="form.classe" required>
            <option value="">Sélectionnez une classe</option>
            <option>6ème</option>
            <option>5ème</option>
            <option>4ème</option>
            <option>3ème</option>
          </select>
        </label>
        <label>
          Série:
          <select v-model="form.serie" required>
            <option value="">Sélectionnez une série</option>
            <option>A</option>
            <option>B</option>
            <option>C</option>
            <option>D</option>
          </select>
        </label>
        <button type="button" @click="$emit('prev-step')">⬅️ Précédent</button>
        <button type="submit">Soumettre</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StepThree',
    data() {
      return {
        form: {
          classe: '',
          serie: ''
        }
      };
    },
    methods: {
      submitForm() {
        this.$emit('submit-form', this.form);
      }
    }
  };
  </script>
  