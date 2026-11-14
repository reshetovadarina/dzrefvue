<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}

function decrement() {
  count.value--
}
</script>

<template>
  <div class="counter">
    <button @click="decrement">−</button>
    <span>{{ count }}</span>
    <button @click="increment">+</button>
  </div>
</template>
