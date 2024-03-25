<script setup>
import { ref } from 'vue';

const campo1 = ref('');
const campo2 = ref('');
</script>

<template>
    <h2>Validación</h2>
    <div class="card col-4 p-3">
        <div class="mb-3">
            <input class="form-control" id="campo_1" type="text" v-model="campo1" placeholder="Campo 1"/>
        </div>
        <div class="mb-3">
            <input class="form-control" id="campo_1" type="text" v-model="campo2" placeholder="Campo 2"/>
        </div>
        <p class="alert alert-success m-0" v-if="campo1 && campo2">Ambos campos están llenos.</p>
        <p class="alert alert-warning m-0" v-else>Completa ambos campos.</p>
    </div>
</template>
