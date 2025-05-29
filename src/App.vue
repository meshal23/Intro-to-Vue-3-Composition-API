<script setup>
import { computed, ref } from "vue";
import socksGreenImage from "./assets/images/socks_green.jpeg";
import socksBlueImage from "./assets/images/socks_blue.jpeg";

const product = ref("Socks");
const brand = ref("Vue Mastery");
const title = computed(() => {
  return brand.value + " " + product.value;
});

const selectedVariant = ref(0);

const details = ref(["50% cotton", "30% wool", "20% polyester"]);

const variants = ref([
  { id: 2234, color: "green", image: socksGreenImage, quantity: 50 },
  { id: 2235, color: "blue", image: socksBlueImage, quantity: 0 },
]);

const image = computed(() => {
  return variants.value[selectedVariant.value].image;
});

const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0;
});

const cart = ref(0);

const addToCart = () => (cart.value += 1);

const updateVariant = (index) => {
  selectedVariant.value = index;
  console.log(index);
};

const onSale = ref(true);
const saleProduct = computed(() => {
  return onSale.value ? `${brand.value + " " + product.value} is on sale` : "";
});
</script>

<template>
  <div class="nav-bar"></div>
  <h1>{{ title }}</h1>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image" />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div
          v-for="(variant, index) in variants"
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        ></div>

        <h1 :style="{ color: red }">{{ saleProduct }}</h1>
        <button
          class="button"
          :class="{ disabledButton: !inStock }"
          :disabled="!inStock"
          v-on:click="addToCart"
        >
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>
