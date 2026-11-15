<script setup>
import { ref, computed } from 'vue'
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


const cart = ref([
  { id: 1, name2: 'Кава', price: 450, qty: 1 },
  { id: 2, name2: 'Молоко мигдальне', price: 95, qty: 2 },
  { id: 3, name2: 'Шоколад чорний з малиною', price: 110, qty: 1 }
])

const totalPrice = computed(() => {
  return cart.value.reduce((sum, item) => sum + item.price * item.qty, 0)
})

function increaseQty(item) {
  item.qty++
}

function decreaseQty(item) {
  if (item.qty > 1) {
    item.qty--
  }
}

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


 <div class="cart">
    <h3>Кошик покупок</h3>
    <ul>
      <li v-for="item in cart" :key="item.id" class="cart-item">
        <span><strong>{{ item.name2 }}</strong> — {{ item.price }} грн</span>

        <div class="controls">
          <button @click="decreaseQty(item)" :disabled="item.qty <= 1">−</button>
          <span>{{ item.qty }} шт.</span>
          <button @click="increaseQty(item)">+</button>
        </div>

        <span>Разом: {{ item.price * item.qty }} грн</span>
      </li>
    </ul>

    <hr />
    <h4>Загальна сума до сплати: {{ totalPrice }} грн</h4>
  </div>

</template>
