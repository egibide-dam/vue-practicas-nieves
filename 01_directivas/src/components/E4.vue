<script setup>
import { ref } from 'vue';

const mostrar = ref(false);

const mostrarOcultar = () => {
    mostrar.value = !mostrar.value;
};
</script>

<template>
    <h2>Mensaje oculto</h2>
    <div class="col-4">
        <p class="alert alert-success" v-if="mostrar">¡Hola, este es un mensaje!</p>
        <button class="btn btn-primary" @click="mostrarOcultar">Mostrar/Ocultar mensaje</button>
    </div>
</template>
