<script setup>
import { ref } from 'vue';

const mensajes = ref([
    {texto: 'Mensaje 1', editando: false},
    {texto: 'Mensaje 2', editando: false},
    {texto: 'Mensaje 3', editando: false},
]);

const iniciarEdicion = (index) => {
    console.log("Iniciando edición del mensaje" + index);
    mensajes.value[index].editando = true;
};

const finalizarEdicion = (index) => {
    console.log("Finalizando edición del mensaje" + index);
    mensajes.value[index].editando = false;
};

const eliminarMensaje = (index) => {
    mensajes.value.splice(index, 1);
};
</script>

<template>
    <h2>Mensajes</h2>
    <div class="col-4">
        <ul class="list-group">
            <li class="list-group-item d-flex justify-content-between align-items-center"
                v-for="(mensaje, index) in mensajes" :key="index">
                <span v-if="!mensaje.editando" v-on:click="iniciarEdicion(index)">{{ mensaje.texto }}</span>
                <input class="form-control bg-success-subtle me-3" v-else v-model="mensaje.texto"
                       @keydown.enter="finalizarEdicion(index)">
                <button class="btn btn-primary" title="Eliminar" @click="eliminarMensaje(index)">
                    <i class="bi bi-trash"></i>
                </button>
            </li>
        </ul>
        <p class="alert alert-danger" v-if="mensajes.length === 0">No hay mensajes disponibles.</p>
    </div>
</template>

<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");
</style>
