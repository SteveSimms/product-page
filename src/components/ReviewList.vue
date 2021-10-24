<script setup>
const props = defineProps({
  reviews: {
    type: Array,
    required: true
  }
})
console.log(props.reviews)
</script>

<template>
<div class="review-container">
<h3>Reviews:</h3>
<ul>
    <li v-for="review in props.reviews"  >
        {{ review.review }}
    </li>
</ul>

</div>

</template>