<script setup>
import { ref } from "vue";
import greenSock from "./assets/images/socks_green.jpeg";

const image = ref(greenSock);
const url = "https://www.google.com/";

const product = ref("Socks");
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <!-- image goes here -->
        <img v-bind:src="image" alt="green sock" />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <a :href="url" target="_blank">visit google.com</a>
      </div>
    </div>
  </div>
</template>
