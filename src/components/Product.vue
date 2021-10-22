<script setup>
import { ref } from 'vue'

const product = 'Infinity Stones'

let image  =  ref('https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.5K6I_uVfKA-nVEkAz4R-pwHaE8%26pid%3DApi&f=1' )

let imageStore = {
    powerStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.5-YOC8OOHRlsj-b-YJB9QAHaE8%26pid%3DApi&f=1',
    realityStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.5Wf6JzkJXCeTAQ98ImCqFAHaE8%26pid%3DApi&f=1'
} 

let cart = ref(0)

let inventory = 0
let inStock = false

let details = ['100% primordial materials', '0% dark magic', 'dark matter included']

let variants = [
    {id:0, name: 'Reality Stone', color: 'Red',universe: 'Earth-616',image: imageStore.realityStone},
    {id:1, name: 'Power Stone', color: 'Purple',universe: 'Earth-616',image: imageStore.powerStone}
    ]

const addToCart = () =>{
    cart.value++

}

const subtractFromCart = () =>{
    cart.value--
}

const updateImage = (variantImage) => {
image.value = variantImage
console.log('image change ')

}





const onSale = false
const sizes = ['S', 'M', 'L', 'XL']

let devloperLinks = {
    marvelAPI: 'https://developer.marvel.com/'
}
</script>

<template>
  <div @click="addToCart" class="cart"> Cart({{ cart }})</div>
<div class="product-display">
    <div class="product-container">
        <div class="product-image">
            <img :src="image">    
        </div>
        <div class="product-info">
            <h1>{{ product }}</h1>
            <p v-if="inventory > 10">In Stock</p>
            <p v-else-if="inventory < 10 && inventory > 0"> Almost Sold Out</p>
                <p v-else>Out of Stock</p>
                <p v-if="onSale"> On Sale </p>
                <ul>
                    <li v-for=" detail in details ">{{ detail }}</li>
                </ul>
                <div v-for="variant of variants" 
                :key="variant.id"
                 @mouseover="updateImage(variant.image)" 
                 class="color-circle"
                 :style="{backgroundColor: variant.color}">
             
                 </div>
                <button 
                @click="addToCart"
                :disabled="!inStock" 
                class="button">Add To Cart </button>
                <button @click="subtractFromCart" class="button">Subtract Cart</button>
        </div>
        <a :href="devloperLinks.marvelAPI">Marvel API</a>
    </div>
</div>


</template>