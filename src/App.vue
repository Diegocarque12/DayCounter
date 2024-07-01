<template>
  <div class="date-checker">
    <h1>Calculadora de días entre fechas</h1>
    <div class="input-group">
      <label for="start-date">Fecha de inicio:</label>
      <input type="date" id="start-date" v-model="startDate">
    </div>
    <div class="input-group">
      <label for="end-date">Fecha de fin:</label>
      <input type="date" id="end-date" v-model="endDate">
    </div>
    <button @click="calculateDays">Calcular días</button>
    <p v-if="daysDifference !== null">
      La diferencia es de {{ daysDifference }} días.
    </p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const startDate = ref('');
const endDate = ref('');
const daysDifference = ref(null);

const calculateDays = () => {
  if (startDate.value && endDate.value) {
    const start = new Date(startDate.value);
    const end = new Date(endDate.value);
    const diffTime = Math.abs(end - start);
    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    daysDifference.value = diffDays;
  } else {
    alert('Por favor, selecciona ambas fechas.');
  }
};
</script>


<style scoped>
.date-checker {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

.input-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input[type="date"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
