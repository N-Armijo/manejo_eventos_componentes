<script setup>
  import { ref } from 'vue'
  import NewUserForm from './NewUserForm.vue'
  import PatientCard from './PatientCard.vue'
  const pacientes = ref([])
  const agregarPaciente = (nuevoPaciente) => {
    pacientes.value.push(nuevoPaciente)
  }
  //eliminar paciente usando index
  const removeCard = (idx) => {
    pacientes.value.splice(idx, 1)
  }
</script>
<template>
  <NewUserForm @submit-form="agregarPaciente" />
  <div v-show="pacientes.length == 0">
    <p :style="{ color: 'red', textAlign: 'center' }">No hay consultas registradas</p>
  </div>
  <div class="pacientes">
    <PatientCard
      v-for="(paciente, idx) in pacientes"
      :key="idx"
      :paciente="paciente.paciente"
      :fecha="paciente.fecha"
      :hora="paciente.hora"
      :gravedad="paciente.gravedad"
      :motivo="paciente.motivo"
      @remove-card="removeCard(idx)"
    />
  </div>
</template>
<style scoped>
  .pacientes {
    margin-top: 2.5rem;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }
</style>
