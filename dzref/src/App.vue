<script setup>
import { ref } from 'vue'
import { reactive } from 'vue'

const count = ref(0)
function increment() {
  count.value++
}
function decrement() {
  count.value--
}


const user = reactive({
  name: '',
  age: 18
})

</script>

<template>

    <div class="counter">
    <button @click="decrement">−</button>
    <span>{{ count }}</span>
    <button @click="increment">+</button>
  </div>


  <div class="user-form">
    <div>
      <label>Ім'я: </label>
      <input v-model="user.name" type="text" placeholder="Введіть ім'я" />
    </div>

    <div>
      <label>Вік: </label>
      <input v-model.number="user.age" type="number" />
    </div>

    <hr />
    <p>Результат: <strong>{{ user.name || 'Анонім' }}</strong>, вік: <strong>{{ user.age }}</strong></p>
  </div>

</template>
