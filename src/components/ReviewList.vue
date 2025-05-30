<script setup>
defineProps({
  reviews: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <h1>Reviews</h1>
  <div class="">
    <ul>
      <li v-for="(review, index) in reviews" :key="index">
        <span>{{ review.name }} given {{ review.rating }} stars</span>
        <br />
        <span>{{ review.content }}</span>
      </li>
    </ul>
  </div>
</template>
