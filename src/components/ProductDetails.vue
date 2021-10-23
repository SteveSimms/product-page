<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    details: {
        type: Array,
        required: true
        
    }
})



</script>

<template>
    <div class="product-details">
                <ul>
                  
                    <li v-for=" detail in props.details ">{{ detail }}</li>
                </ul>
                </div>

</template>