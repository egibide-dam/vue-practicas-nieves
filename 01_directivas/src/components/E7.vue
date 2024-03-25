<script setup>
import { ref } from 'vue';

const contador = ref(0);

const incrementar = () => {
    contador.value++;
};

const decrementar = () => {
    contador.value--;
};
</script>

<template>
    <h2>Contador</h2>
    <div class="col-4">
        <p class="alert alert-info" v-if="contador === 0">El contador es igual a cero. </p>
        <p class="alert alert-success" v-else-if="contador > 0">El contador es positivo: {{ contador }}</p>
        <p class="alert alert-warning" v-else-if="contador < 0">El contador es negativo: {{ contador }}</p>
        <p class="alert alert-danger" v-else>El contador es desconocido.</p>

        <button class="btn btn-primary me-2" title="Incrementar el contador" @click="incrementar">
            <i class="bi bi-plus-lg"></i>
        </button>
        <button class="btn btn-primary" title="Decrementar el contador" @click="decrementar">
            <i class="bi bi-dash-lg"></i>
        </button>
    </div>
</template>

<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");
</style>
