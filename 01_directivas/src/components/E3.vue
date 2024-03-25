<script setup>
import { ref, computed } from 'vue';

// Variable reactiva para el mensaje
const nuevoMensaje = ref('');

// Propiedad computada para contar caracteres
const contarCaracteres = computed(() => nuevoMensaje.value.length);

// Mensaje a mostrar
const mensaje = computed(() => {
    if (contarCaracteres.value === 0) {
        return 'Escribe algo...';
    } else {
        return 'Mensaje: ' + nuevoMensaje.value;
    }
});
</script>

<template>
    <h2>Contar caracteres</h2>
    <div class="card col-4 p-3">
        <div class="mb-3">
            <label class="form-label" for="mensaje">Mensaje</label>
            <input class="form-control" id="mensaje" type="text" v-model="nuevoMensaje"
                   placeholder="Escribe un mensaje"/>
        </div>
        <div class="alert alert-warning m-0 d-flex justify-content-between align-items-center">
            <span>{{ mensaje }}</span>
            <span class="badge text-bg-primary rounded-pill">{{ contarCaracteres }}</span>
        </div>
    </div>
</template>
