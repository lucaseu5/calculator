<template>
  <div class="container text-center mt-5">
    <h1 class="bg-primary rounded-3 mb-5 p-3">Calculadora Aritmética</h1>
    <div class="container">
      <input v-model.number="numero1" type="number" placeholder="Número 1" class="p-2 input-field me-3 border-3 border-primary rounded-3 focus-ring focus-ring-light"/>
      <select v-model="operacao" class="p-2 rounded-3 border-primary border-3 focus-ring focus-ring-light">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input v-model.number="numero2" type="number" placeholder="Número 2" class="p-2 ms-3 border-3 border-primary rounded-3 focus-ring focus-ring-light"/>
    </div>
    <div v-if="resultado !== null">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
      resultado: null,
    };
  },
  watch: {
    numero1: 'calcular',
    numero2: 'calcular',
    operacao: 'calcular',
  },
  methods: {
    calcular() {
      const num1 = parseFloat(this.numero1);
      const num2 = parseFloat(this.numero2);
      switch (this.operacao) {
        case '+':
          this.resultado = num1 + num2;
          break;
        case '-':
          this.resultado = num1 - num2;
          break;
        case '*':
          this.resultado = num1 * num2;
          break;
        case '/':
          this.resultado = num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
          break;
        default:
          this.resultado = null;
      }
    },
  },
};
</script>

<style>
</style>