<script setup>
import { ref } from 'vue'

import ProductDisplay from './components/ProductDisplay.vue'
import NavBar from './components/NavBar.vue'
let cart = ref([])
let premium = true //passing premium to ProductDisplay component

//function that houses our main logic
const updateCart = (id) =>{
  cart.value.push(id)
  console.log(cart.value)
  
}

const subtractFromCart = () =>{
    cart.value--
}

//Sending the prop successfully
</script>

<template>
<NavBar />
 <div  class="cart"> Cart({{ cart.length }})</div>

<ProductDisplay :premium="premium" @addTocart="updateCart" @subtractFromCart="subtractFromCart"/> 
<!-- <ProductDisplay @addTocart="getAddedItems" @subtractFromCart="subtractFromCart"/>
<ProductDisplay @addTocart="getAddedItems" @subtractFromCart="subtractFromCart"/> -->

</template>

<style>

</style>
