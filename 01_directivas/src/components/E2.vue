<script setup>
import { ref } from 'vue';

// Variables reactivas
const titulo = ref('Practica con v-bind');
const mensaje = ref('Este es un ejemplo práctico con v-bind en Vue 3.');

// Clase dinámica con v-bind:class
const claseTitulo = ref('titulo-grande');

// Estilos dinámicos con v-bind:style
const estilosParrafo = ref({
    color: 'teal',
    fontSize: '16px',
});

// Enlace dinámico con v-bind:href y v-bind:target
const enlace = ref({
    url: 'https://example.org',
    texto: 'Ir al ejemplo',
    target: '_blank',
});
</script>

<template>
    <h2 :class="claseTitulo">{{ titulo }}</h2>
    <p :style="estilosParrafo">{{ mensaje }}</p>
    <a class="link-primary link-underline-opacity-0 link-underline-opacity-100-hover"
       :href="enlace.url" :target="enlace.target">{{ enlace.texto }}</a>
</template>

<style scoped>
/* Estilo dinámico con v-bind:class */
.titulo-grande {
    font-size: 400%;
}
</style>
