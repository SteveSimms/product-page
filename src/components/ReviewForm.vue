<script>
import { ref } from 'vue'
export let name = ref('')
export let review = ref('')
export let rating = ref(0)
export let recommendation = ref('')

export let productReview = ref(
{
        name: name.value,
        review: review.value,
        rating: rating.value,
        recommendation: recommendation.value
}

)



export default {}

</script>


<script setup>
import { ref } from 'vue'
// Had to define props in a seperate regular script tag and pass it to set up  
defineProps({
review: {
    type: Object,
    default: productReview.value

}
})

 


 

// const emits = defineEmits(['reviewSubmitted', productReview.value])
const onSubmit = () =>{
//Had to duplicate code from above script tag to get the data passed down 
if(name.value ===  '' || review.value === '' || rating.value === null){
    alert('Review is incomplete. Please fill out every field.')
    return

}
 let productReview = ref(
{
        name: name.value,
        review: review.value,
        rating: rating.value,
        recommendation: recommendation.value
})

     
    console.log(productReview.value)
      emits('reviewSubmitted', productReview.value)
    document.querySelector('.review-form').reset()
 
}

const emits = defineEmits(['reviewSubmitted', productReview.value])
</script>


<template>
<form @submit.prevent="onSubmit" class="review-form">
<h3>
Leave A Review
</h3> 
<label  for="name">Name:</label> 
<input v-model="name" id="name" type="text">

<label for="review">Review:</label> 
<textarea v-model="review" id="review" cols="30" rows="10"></textarea>
<label for="rating">Rating:</label> 
<select v-model.number="rating" id="rating">
<option>5</option>
<option>4</option>
<option>3</option>
<option>2</option>
<option>1</option>

</select>
<label  for="name">Would you reccomend this product?</label> 
<input v-model="recommendation" id="recommendation" type="text">
<input  class="button" type="submit" value="Submit">

</form> 


</template>