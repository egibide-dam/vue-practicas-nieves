<script setup>
import { ref } from 'vue';

const items = ref(['Elemento 1', 'Elemento 2', 'Elemento 3']);
//const items = ref('');
</script>

<template>
    <h2>Lista de elementos</h2>
    <div class="col-4">
        <ul class="list-group" v-if="items.length > 0">
            <li class="list-group-item" v-for="(item, index) in items" :key="index">{{ item }}</li>
        </ul>
        <p class="alert alert-danger" v-else>No hay elementos en la lista.</p>
    </div>
</template>
