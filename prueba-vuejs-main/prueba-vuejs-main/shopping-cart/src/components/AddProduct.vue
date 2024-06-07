<script setup>
import { ref, defineEmits } from "vue"

const newProduct = ref({id: "", nombre: "", precio: 0, category: "fruta"})
const emit = defineEmits(["add"]) 

function generateId() {
 return Math.random().toString(36).substring(2, 10);
}

function resetProduct() {
    newProduct.value = {id: "", nombre: "", precio: 0, category: "fruta"}
}

function addProduct() {
    newProduct.value.id = generateId()
    emit("add", newProduct.value)
    resetProduct()
}

</script>

<template>
     <section>
        <div><h1>Añadir Productos</h1></div>
        <div>
        <input type="text" v-model="newProduct.nombre" placeholder="Entre el nombre del producto">
        <input type="number" v-model="newProduct.precio" placeholder="Entre el precio del producto">
        <select v-model="newProduct.category">
            <option value="fruta">Fruta</option>
            <option value="verdura">Verdura</option>
        </select>
        <button @click="addProduct">Añadir producto</button>
        </div>
    </section>
</template>

<style scoped>
</style>