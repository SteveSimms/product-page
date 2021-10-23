<script setup>
import { ref } from 'vue'

import ProductDisplay from './components/ProductDisplay.vue'
import NavBar from './components/NavBar.vue'
let cart = ref(0)
let premium = true //passing premium to ProductDisplay component


const getAddedItems = () =>{
  cart.value++
  console.log(cart.value)
  
}
//Sending the prop successfully
</script>

<template>
<NavBar />
 <div  class="cart"> Cart({{ cart }})</div>

<ProductDisplay :premium="premium" @addTocart="getAddedItems"/> 
<ProductDisplay @addTocart="getAddedItems"/>
<ProductDisplay @addTocart="getAddedItems"/>

</template>

<style>

</style>
