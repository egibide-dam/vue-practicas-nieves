<script setup>
import { ref } from 'vue';

const productos = [
    {id: 1, nombre: 'Producto A'},
    {id: 2, nombre: 'Producto B'},
    {id: 3, nombre: 'Producto C'},
];

const carrito = ref([]);

const nuevoProducto = ref(productos[0].id);

const agregarProducto = () => {
    const productoExistente = carrito.value.find(item => item.id === nuevoProducto.value);

    if (productoExistente) {
        productoExistente.cantidad++;
    } else {
        carrito.value.push({id: nuevoProducto.value, nombre: getNombreProducto(nuevoProducto.value), cantidad: 1});
    }
};

const getNombreProducto = (productoId) => {
    const producto = productos.find(item => item.id === productoId);
    return producto ? producto.nombre : 'Desconocido';
};

const incrementarCantidad = (index) => {
    carrito.value[index].cantidad++;
};

const decrementarCantidad = (index) => {
    if (carrito.value[index].cantidad > 1) {
        carrito.value[index].cantidad--;
    } else {
        // Si la cantidad es 1 o menos, elimina el producto del carrito
        carrito.value.splice(index, 1);
    }
};

const eliminarProducto = (index) => {
    carrito.value.splice(index, 1);
};
</script>

<template>
    <h2>Carrito de la compra</h2>
    <div class="col-6">
        <ul class="list-group">
            <li class="list-group-item d-flex justify-content-between align-items-center"
                v-for="(producto, index) in carrito" :key="index">
                <span>{{ producto.nombre }}</span>
                <span class="badge text-bg-primary rounded-pill">{{ producto.cantidad }}</span>

                <div>
                    <button class="btn btn-secondary me-2" title="Incrementar cantidad"
                            @click="incrementarCantidad(index)">
                        <i class="bi bi-plus-lg"></i>
                    </button>
                    <button class="btn btn-secondary me-2" title="Decrementar cantidad"
                            @click="decrementarCantidad(index)">
                        <i class="bi bi-dash-lg"></i>
                    </button>
                    <button class="btn btn-secondary" title="Eliminar" @click="eliminarProducto(index)">
                        <i class="bi bi-trash"></i>
                    </button>
                </div>
            </li>
        </ul>
        <p class="alert alert-danger" v-if="carrito.length === 0">El carrito está vacío.</p>
    </div>

    <h3 class="mt-3">Productos disponibles</h3>
    <div class="col-6">
        <div class="row">
            <div class="col">
                <select class="form-select" v-model="nuevoProducto">
                    <option v-for="producto in productos" :key="producto.id" :value="producto.id">
                        {{ producto.nombre }}
                    </option>
                </select>
            </div>
            <div class="col-auto">
                <button class="btn btn-primary" @click="agregarProducto">Agregar al carrito</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");
</style>
