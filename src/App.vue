<script setup>
import { ref } from "vue";
const product = ref("boots");
const description = ref("this is my description");
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>
