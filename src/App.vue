<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

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
    <Cabecalho :estado="estado" />
    <Formulario :estado="estado" :calculaResultado="calculaResultado" />
  </div>
</template>


<style scoped>
.form-control{
  width: 180px;
}



</style>
