<script setup>

defineProps({
  paciente: String,
  fecha: String,
  hora: String,
  gravedad: String,
  motivo: String,
  idx: Number
});

// Definir emit para eventos
const emit = defineEmits(['remove-card']);

// Función para emitir el evento de eliminar
const removeCard = () => {
  emit('remove-card');
}
</script>
<template>
  <div
    class="card"
    :class="gravedad === 'Baja' ? 'green' : gravedad === 'Media' ? 'yellow' : 'red'"
  >
    <b>Paciente</b>
    <p>{{ paciente }}</p>
    <b>Fecha</b>
    <p>{{ fecha }}</p>
    <b>Hora</b>
    <p>{{ hora }}</p>
    <b>Motivo</b>
    <p>{{ motivo }}</p>
    <button @click="removeCard">Eliminar</button>
  </div>
</template>
<style scoped>
.card {
  min-width: 10rem;
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
}

.yellow {
  background-color: #f7f781;
}
.green {
  background-color: #8ce28c;
}
.red {
  background-color: #ee7d7d;
}
</style>
