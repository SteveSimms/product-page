<script setup>
const props = defineProps({ // Define the props in the component you want to send data from  then use it below in the template
    details: {
        type: Array,
        required: true
        
    }
})
console.log(props.details)


</script>

<template>
    <div class="product-details">
                <ul>
                    <li v-for=" detail in props.details ">{{ detail }}</li>
                </ul> 
            
                </div>

</template>