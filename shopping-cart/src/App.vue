<script setup>
import { ref } from 'vue'

const products = ref([
  {id: 12857, nombre: "manzana", precio: 2},
  {id: 23756, nombre: "platano", precio: 1.5}
])

function generateId() {
 return Math.random().toString(36).substring(2, 10);
}


const newProduct = ref({id: "", nombre: "", precio: 0})
const editedProduct = ref(null)

function addProducto() {
  newProduct.value = {id: generateId(), nombre: nombre.value, precio: precio.value}
  products.value.push(newProduct.value)
  nombre.value = ""
  precio.value = 0
}

function deleteProduct(id) {
  const productIndex = products.value.findIndex(item => item.id === id)
  console.log(id)
  products.value.splice(productIndex, 1)
}

function editProduct(id) {
  const currentProduct = products.find(item => item.id === id)
  editedProduct = {id: currentProduct.value.id, nombre: currentProduct.value.nombre, precio: currentProduct.value.precio}
}

</script>

<template>
  <section>
    <div><h1>Añadir Productos</h1></div>
    <div>
      <input type="text" v-model="nombre" placeholder="Entre el nombre del producto">
      <input type="number" v-model="precio" placeholder="Entre el precio del producto">
      <button @click="addProducto">Añadir producto</button>
    </div>
  </section>

  <section>
    <div><h1>Listo Productos</h1></div>
    <div>
      <u>
        <li v-for="(product, index) in products" :key="index">
          {{ product.id }} - {{ product.nombre }} - {{ product.precio }}
          <button @click="deleteProduct(product.id)">X</button>
          <button @click="editProduct(product.id)">Editer</button>
        </li>
      </u>
    </div>
  </section>

  <section v-if="editedProduct">
    <div><h1>Editar Productos</h1></div>
    <div>
      <input type="text" v-model="newNombre" placeholder="Entre el nuevo nombre del producto">
      <input type="number" v-model="newPrecio" placeholder="Entre el nuevo precio del producto">
      <button @click="editProduct()">Añadir producto</button>
    </div>
  </section>
</template>

<style scoped>

</style>
