<template>

  <div>
    <!--Exercice3-->
      <button @click="activateTab = 'TabA'">Tab A</button>
  <button @click="activateTab = 'TabB'">Tab B</button>
  <button @click="activateTab = 'TabC'">Tab C</button>
  <keep-alive>
<component :is="activateTab"></component>
</keep-alive> 

<Teleport to="#portal-root"> 
      <PortalApp></PortalApp>
    </Teleport>

<!--Exercice2-->

    <div>
    <h2>Tableau des utilisateurs</h2>
    <DataTable :columns="columns" :rows="users">
      <!-- Personnalisation de l'en-tête de la colonne 'name' -->
      <template #header-name>
        <span style="color: blue;">Nom</span>
      </template>

      <!-- Personnalisation de la cellule 'name' -->
      <template #cell-name="{ row }">
        <strong>{{ row.name.toUpperCase() }}</strong>
      </template>

      <!-- Personnalisation de la cellule 'email' -->
      <template #cell-email="{ row }">
        <a :href="`mailto:${row.email}`">{{ row.email }}</a>
      </template>
    </DataTable>
  </div>


  <!--Exercice1-->
  <component
      :is="currentComponent"
      @next-step="handleNextStep"
      @prev-step="handlePrevStep"
      @submit-form="handleSubmit"
    ></component>
  </div> 
  
  
</template>

<script>
import TabA from './components/TabA.vue';
import TabB from './components/TabB.vue';
import TabC from './components/TabC.vue';
import PortalApp from './components/PortalApp.vue';
import DataTable from './components/Exercice2/DataTable.vue';
import Step1App from './components/Exercice1/Step1App.vue';
import Step2App from './components/Exercice1/Step2App.vue';
import Step3App from './components/Exercice1/Step3App.vue';

export default {
  name: 'App',
  components: {
    TabA,
    TabB,
    TabC,
    PortalApp,
    DataTable,
    Step1App,
    Step2App,
    Step3App,
  },
  data() {
    return {
      activateTab: 'TabA',
      columns: [
        { key: 'name', label: 'Nom' },
        { key: 'email', label: 'Email' },
        { key: 'age', label: 'Âge' }
      ],
      users: [
        { name: 'Alice', email: 'alice@example.com', age: 25 },
        { name: 'Bob', email: 'bob@example.com', age: 30 },
        { name: 'Charlie', email: 'charlie@example.com', age: 35 }
      ],
      currentStep: 1,
      formData: {
        nom: '',
        prenom: '',
        email: '',
        telephone: '',
        classe: '',
        serie: ''
      }
    };
  },
  computed: {
    currentComponent() {
      switch (this.currentStep) {
        case 1:
          return 'Step1App';
        case 2:
          return 'Step2App';
        case 3:
          return 'Step3App';
        default:
          return 'Step1App';
      }
    }
  },
  methods: {
    handleNextStep(data) {
      this.formData = { ...this.formData, ...data };
      if (this.currentStep < 3) {
        this.currentStep++;
      }
    },
    handlePrevStep() {
      if (this.currentStep > 1) {
        this.currentStep--;
      }
    },
    handleSubmit(data) {
      this.formData = { ...this.formData, ...data };
      console.log('Données du formulaire:', this.formData);
      alert('Formulaire soumis avec succès!');
      this.currentStep = 1;
      this.formData = {
        nom: '',
        prenom: '',
        email: '',
        telephone: '',
        classe: '',
        serie: ''
      };
    }
  }
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
