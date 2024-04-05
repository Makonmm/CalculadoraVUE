<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: '',
  num2: '',
  operacoes: {
    somar: (a, b) => a + b,
    subtrair: (a, b) => a - b,
    dividir: (a, b) => (b !== 0 ? a / b : 'Não podemos dividir por zero'),
    multiplicar: (a, b) => a * b, 
  },
  resultado: 0,
})

const calculaResultado = () => {
  const { num1, num2, operacao } = estado
  estado.resultado = estado.operacoes[operacao](parseFloat(num1), parseFloat(num2));
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-success rounded-6">
      <h1 class="text-center color text-light">Calculadora Aritmética</h1>
    </header>
    <form class="p-5 mb-4 mt-4">
      <div class="row">
        <input v-model="estado.num1" type="number" placeholder="Digite um número" class="form-control p-2 me-4 mb-4" @input="calculaResultado()">
        <input v-model="estado.num2" type="number" placeholder="Digite outro número" class="form-control p-2 me-4 mb-4" @input="calculaResultado()">
        <div class="col-md-2">
          <select v-model="estado.operacao" @change="calculaResultado()" class="form-control">
            <option value="somar">Somar</option>
            <option value="subtrair">Subtrair</option>
            <option value="dividir">Dividir</option>
            <option value="multiplicar">Multiplicar</option>
          </select>
        </div>
      </div>
    </form>
    
    <div class="resultado  ms-5" v-if="estado.resultado !== null">
      <p>Resultado: {{ estado.resultado }}</p>
    </div>
  </div>
</template>

<style scoped>
.form-control{
  width: 180px;
}



</style>
