<script setup>
import { ref, computed } from 'vue';

// Declarar variables reactivas para nombre y apellido
const nombre = ref('Ana');
const apellido = ref('García');

// Propiedad computada para el nombre completo
const nombreCompleto = computed(() => {
    return `${nombre.value} ${apellido.value}`;
});
</script>

<template>
    <h2>Datos personales</h2>
    <div class="card col-4 p-3">
        <div class="mb-3">
            <label class="form-label" for="nombre">Nombre</label>
            <input class="form-control" id="nombre" type="text" v-model="nombre"/>
        </div>
        <div class="mb-3">
            <label class="form-label" for="apellido">Apellido</label>
            <input class="form-control" id="apellido" type="text" v-model="apellido"/>
        </div>
        <p class="alert alert-warning m-0">Tu nombre completo es: {{ nombreCompleto }}</p>
    </div>
</template>
