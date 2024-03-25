<script setup>
import { ref } from 'vue';

const tareas = ref([
    {nombre: 'Hacer la compra', completada: false},
    {nombre: 'Hacer ejercicio', completada: true},
    {nombre: 'Leer un libro', completada: false},
]);

const cambiarEstadoTarea = (index) => {
    const tarea = tareas.value[index];
    if (tarea.completada) {
        tareas.value.splice(index, 1); // Elimina la tarea completada del array
    } else {
        tarea.completada = true;
    }
};
</script>

<template>
    <h2>Lista de tareas</h2>
    <div class="col-4">
        <ul class="list-group">
            <li class="list-group-item d-flex justify-content-between align-items-center"
                v-for="(tarea, index) in tareas" :key="index" @dblclick="cambiarEstadoTarea(index)">
                <span>{{ tarea.nombre }}</span>
                <template v-if="tarea.completada">
                    <span class="badge text-bg-secondary rounded-pill">Completada</span>
                </template>
                <template v-else>
                    <span class="badge text-bg-primary rounded-pill">Pendiente</span>
                </template>
            </li>
        </ul>
        <p class="alert alert-danger" v-if="tareas.length === 0">No hay tareas disponibles.</p>
    </div>
</template>
