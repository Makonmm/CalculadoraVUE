
<script setup>
    const props = defineProps(['estado', 'calculaResultado'])
</script>

<template>
        <form class="p-5 mb-4 mt-4">
        <div class="row">
            <input v-model="props.estado.num1" type="number" placeholder="Digite um número" class="form-control p-2 me-4 mb-4" @input="props.calculaResultado">
            <input v-model="props.estado.num2" type="number" placeholder="Digite outro número" class="form-control p-2 me-4 mb-4" @input="props.calculaResultado">
            <div class="col-md-2">
            <select v-model="props.estado.operacao" @change="props.calculaResultado" class="form-control">
                <option value="somar">Somar</option>
                <option value="subtrair">Subtrair</option>
                <option value="dividir">Dividir</option>
                <option value="multiplicar">Multiplicar</option>
            </select>
            </div>
        </div>
        </form>
    
        <div class="resultado  ms-5" v-if="props.estado.resultado !== null">
        <p>Resultado: {{ props.estado.resultado }}</p>
        </div>
    </template>
    
    <style scoped>
    .form-control {
        width: 180px;
    }
    </style>