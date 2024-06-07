<script setup>
import {ref, defineProps, defineEmits} from 'vue'

const props = defineProps({
    products: {
        type: Array,
        default: []
    }
})

const emit = defineEmits(["remove", "edit"])

const currentCategory = ref("fruta")

const filteredProduct = conputed((category) => {
    return props.products.filter(item => item.category === category.value)
})

function deleteProduct(id) {
    emit("remove", id)
}

function editProduct(id) {
    emit("edit", id)
}

</script>

<template>
    <section>
        <div><h1>Listo Productos</h1></div>
        <div>
          <div>
            <button @click="currentCategory = 'todos'">Todos</button>
            <button @click="currentCategory = 'fruta'">Frutas</button>
            <button @click="currentCategory='verdura'">Verduras</button>
          </div>
          <u>
            <li v-for="(product, index) in filteredProduct(currentCategory)" :key="index">
              {{ product.id }} - {{ product.nombre }} - {{ product.precio }} - {{ product.category }}
              <button @click="deleteProduct">X</button>
              <button @click="editProduct">Editar</button>
            </li>
          </u>
        </div>
      </section>
</template>

<style lang="scss" scoped>

</style>