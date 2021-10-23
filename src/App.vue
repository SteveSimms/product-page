<script setup>
import { ref } from 'vue'

import ProductDisplay from './components/ProductDisplay.vue'
import NavBar from './components/NavBar.vue'
let cart = ref(0)
let premium = true //passing premium to ProductDisplay component

//Sending the prop successfully
</script>

<template>
<NavBar />
 <div  class="cart"> Cart({{ cart }})</div>

<ProductDisplay :premium="premium"/> 
<ProductDisplay />
<ProductDisplay />

</template>

<style>

</style>
