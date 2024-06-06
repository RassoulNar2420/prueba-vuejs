<script setup>
import { computed, ref } from 'vue'
import AddProduct from '@/components/AddProduct.vue'
import ListProduct from '@/components/ListProduct.vue'

const products = ref([
  {id: 12857, nombre: "manzana", precio: 2, category: "fruta"},
  {id: 23756, nombre: "platano", precio: 1.5, category: "fruta"},
  {id: 23756, nombre: "límon", precio: 1.5, category: "verdura"}
])
const nombre = ref(null)
const precio = ref(0)
const category = ref("fruta")
const currentCategory = ref("todos")


const currentProduct = ref(null)
const editedProduct = ref(null)
const total = computed(() => products.value.reduce((prev, curr) => prev + curr.precio, 0))

function addProduct(product) {
  products.value.push(product)
}

function deleteProduct(id) {
  const productIndex = products.value.findIndex(item => item.id === id)
  console.log(id)
  products.value.splice(productIndex, 1)
}

function editProduct(id) {
  currentProduct.value = products.value.find(item => item.id === id) 
  editedProduct.value = {id: currentProduct.value.id, nombre: currentProduct.value.nombre, precio: currentProduct.value.precio}
}

function valideEditionProduct(id){
  const currentProductIndex = products.value.findIndex(item => item.id === id)
  products.value[currentProductIndex] = {id: editedProduct.value.id, nombre: editedProduct.value.nombre, precio: editedProduct.value.precio}
  editedProduct.value.nombre = ""
  editedProduct.value.precio = 0
}

function filteredProduct(category) {
  if (currentCategory.value === "todos") {
    return products.value
  } else {
    return products.value.filter(item => item.category === category)
  }
}

</script>

<template>

  <AddProduct @add="addProduct" />
  <ListProduct :products="products" @edit="editProduct"  @remove="deleteProduct" />

  <section v-if="editedProduct">
    <div><h1>Editar Productos<button @click="editedProduct=null">Salir</button></h1></div>
    <div>
      <input type="text" v-model="editedProduct.nombre" placeholder="Entre el nuevo nombre del producto">
      <input type="number" v-model="editedProduct.precio" placeholder="Entre el nuevo precio del producto">
      <button @click="valideEditionProduct(editedProduct.id)">Editar producto</button>
    </div>
  </section>

  <section>
    <h1>Total : {{ total }}€</h1>
  </section>
</template>

<style scoped>

</style>
