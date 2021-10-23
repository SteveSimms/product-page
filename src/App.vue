<script setup>
import { ref, defineProps } from 'vue'
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Product from './components/Product.vue'
import NavBar from './components/NavBar.vue'
let cart = ref(0)
let premium = true
// let props = defineProps({
//   cart: {
//     type: Number,
//     default: 0
//   }
// })

</script>

<template>
<NavBar />
 <div  class="cart"> Cart({{ cart }})</div>

<Product :premium="premium"/>
<Product />
<Product />

</template>

<style>

</style>
