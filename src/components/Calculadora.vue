<script setup>
import { reactive } from 'vue';

const estado = reactive({
    operacao: 'soma',
    numeroA: 0,
    numeroB: 0,
    resultado: 0,
})

function multi() {
    return estado.resultado = parseFloat(estado.numeroA) * parseFloat(estado.numeroB);
}

function div() {
    if (estado.numeroB === 0) {
        alert('Não é possível dividir por 0')
        return estado.resultado = 'Não existe'
    }
    return estado.resultado = parseFloat(estado.numeroA) / parseFloat(estado.numeroB);
}

function soma() {
    return estado.resultado = parseFloat(estado.numeroA) + parseFloat(estado.numeroB);
}

function sub() {
    return estado.resultado = parseFloat(estado.numeroA) - parseFloat(estado.numeroB);
}

function res(evento) {
    switch (estado.operacao) {
        case 'multiplicacao':
            return multi();
        case 'subtracao':
            return sub();
        case 'divisao':
            return div();
        default:
            return soma();
    }
}

</script>

<template>
    <header class="row">
        <div class="container bg-light text-center">
            <h1>Calculadora Aritimética</h1>
        </div>
    </header>
    <div class="row container mt-4 mx-auto">
        <div class="col-md d-flex justify-content-center">
            <input v-model="estado.numeroA" @input="res" class="me-2" type="text" placeholder="Digite primeiro número">
            <input v-model="estado.numeroB" @input="res" class="me-2" type="text" placeholder="Digite o segundo número">
            <span>{{ estado.resultado }}</span>
        </div>
        <div class="row text-center">
            <div class="col-md-3 mx-auto mt-2">
                <select v-model="estado.operacao" @change="res">
                    <option value="soma">Soma</option>
                    <option value="subtracao">Subtração</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                </select>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
