<script setup>
import { ref, computed } from 'vue'
import  ProductDetails  from '../components/ProductDetails.vue'
import App from '../App.vue'

// product-page\src\components\ProductDetails.vue

//    import CryptoData from "@/components/CryptoData.vue";
const props = defineProps({
  premium: {
    type: Boolean,
    required: true
  }
})
const product = 'Infinity Stones'

const brand = 'V:' 
 
// let image  =  ref('https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.5K6I_uVfKA-nVEkAz4R-pwHaE8%26pid%3DApi&f=1' )

let selectedVariant = ref(0)

let imageStore = {
    powerStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.5-YOC8OOHRlsj-b-YJB9QAHaE8%26pid%3DApi&f=1',
    realityStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.5Wf6JzkJXCeTAQ98ImCqFAHaE8%26pid%3DApi&f=1',
    timeStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.uOFmttU91qS0iJ4PO-7DzgHaE8%26pid%3DApi&f=1',
    spaceStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.dYgjqoFq9FGLN5Tqi8om8AHaEo%26pid%3DApi&f=1',
    mindStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.UiXkBkmkDxCtnBGdL5_2YgHaE8%26pid%3DApi&f=1',
    soulStone: 'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.ljPUujzTRz0864CiAL0zPwHaEK%26pid%3DApi&f=1'
} 

// let cart = ref(0)

let inventory = 0


let details = ['100% primordial materials', '0% dark magic', 'dark matter included']

let variants = [
    {id:0, name: 'Reality Stone', color: 'Red',universe: 'Earth-616',image: imageStore.realityStone,quantity: 10, onSale: false},
    {id:1, name: 'Power Stone', color: 'Purple',universe: 'Earth-616',image: imageStore.powerStone, quantity: 4, onSale: false},
    {id:2, name: 'Time Stone', color: 'Green',universe: 'Earth-616',image: imageStore.timeStone,quantity: 0, onSale: false},
    {id:3, name: 'Space Stone', color: 'Blue',universe: 'Earth-616',image: imageStore.spaceStone,quantity: 4, onSale: true},
    {id:4, name: 'Mind Stone', color: 'Yellow',universe: 'Earth-616',image: imageStore.mindStone, quantity: 1, onSale: true},
    {id:5, name: 'Soul Stone', color: 'Orange',universe: 'Earth-616',image: imageStore.soulStone, quantity: 0, onSale: false}
    ]
// defineEmits from the component that you want to send the event from eventOrigin > eventName
const emits = defineEmits(['addToCart','subtractFromCart'])
// Supposed to be emitting events 
// event handler
const addToCartHandler = () =>{
  // call this event with click handler where you need it 
     emits('addTocart', variants[selectedVariant.value].id)
     console.log(variants[selectedVariant.value].id)

}


const subtractFromCartHandler = () =>{
    emits('subtractFromCart')
}



let productBrand = computed(() => {
    return `${brand} 
           ${product}`
})

let updateVariant = (index) => {
    selectedVariant.value = index
}

let image = computed(() => {
    return variants[selectedVariant.value].image
})

let inStock = computed(()=>{
    return variants[selectedVariant.value].quantity

})

let itemOnSale = computed(()=>{
    return variants[selectedVariant.value].onSale

})

let displayVariantName = computed(()=>{
    return variants[selectedVariant.value].name

})

let shipping = computed(()=>{
        if(props.premium){ // need to use props before the prop name
            return 'Free'
        }
        return 2.99
})


const onSale = ref(true) 

let sale = computed(() => {
if(onSale.value == true){
    return ` ${brand} ${product}: ${variants[selectedVariant.value].name} is on sale`
}

return ''
})
console.log('variants.name',variants)

const sizes = ['S', 'M', 'L', 'XL']

let devloperLinks = {
    marvelAPI: 'https://developer.marvel.com/'
}
</script>

<template>
  <!-- <div  class="cart"> Cart({{ cart }})</div> -->
 
<div class="product-display">
    <div class="product-container">
        <div class="product-image">
            <img :src="image"  :class="{'out-of-stock-img': !inStock  }">    
        </div>
        <div class="product-info">
            <h1>{{ productBrand }}</h1>
            <p v-if="inStock">In Stock: {{ displayVariantName }}</p>
                <p v-else>Out of Stock: {{ displayVariantName }}</p>
                <p>Shipping: {{ shipping }}</p>
                <p v-if="itemOnSale"> {{ sale }} </p>
           
               
                    <ProductDetails :details="details" />
                
               
                <div v-for="(variant,index) of variants" 
                :key="variant.id"
                 @mouseover="updateVariant(index)"
                 class="color-circle"
                 :style="{backgroundColor: variant.color}">
                   
                 </div>
                 
                <button 
                @click="addToCartHandler"
                :class="{disabledButton: !inStock}"
                :disabled="!inStock" 
                class="button">Add To Cart </button>
                <button @click="subtractFromCartHandler" class="button">Subtract Cart</button>
        </div>
        <a :href="devloperLinks.marvelAPI">Marvel API</a>
    </div>
</div>


</template>