<script setup>
import { reactive, computed } from 'vue';


const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: 'soma', 
});


const resultado = computed(() => {

  const { numero1, numero2, operacao } = estado;

  switch (operacao) {
    case 'soma':
      return numero1 + numero2;
    case 'subtracao':
      return numero1 - numero2;
    case 'multiplicacao':
      return numero1 * numero2;
    case 'divisao':
      
      if (numero2 === 0) {
        return 'Não é possível dividir por zero';
      }
      return numero1 / numero2;
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container">
    <header>
      <h1>Calculadora Aritmética Vue.js</h1>
    </header>
    <main class="calculadora">
      <div class="campos">
        <input type="number" placeholder="Número 1" v-model.number="estado.numero1" />

        <select v-model="estado.operacao" class="operador">
          <option value="soma">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">×</option>
          <option value="divisao">÷</option>
        </select>

        <input type="number" placeholder="Número 2" v-model.number="estado.numero2" />
      </div>
      <div class="resultado">
        <h2>Resultado: {{ resultado }}</h2>
      </div>
    </main>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 40px auto;
  font-family: Arial, sans-serif;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

header {
  text-align: center;
  color: #2c3e50;
  border-bottom: 2px solid #ddd;
  padding-bottom: 10px;
  margin-bottom: 20px;
}

.calculadora {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.campos {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
}

input[type="number"],
select {
  width: 100%;
  padding: 12px;
  font-size: 1.2em;
  border-radius: 6px;
  border: 1px solid #ccc;
  text-align: center;
}

.operador {
  flex-grow: 0;
  flex-shrink: 0;
  width: auto;
  min-width: 60px;
  font-weight: bold;
}

.resultado {
  background-color: #e0f7fa;
  border: 1px solid #4dd0e1;
  padding: 20px;
  text-align: center;
  border-radius: 6px;
}

.resultado h2 {
  margin: 0;
  color: #00796b;
  font-size: 1.8em;
  word-wrap: break-word;
}
</style>