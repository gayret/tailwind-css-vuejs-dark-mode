<script setup>
import { reactive } from '@vue/reactivity'

const state = reactive({
  theme: 'light',
  count: 0,
})

const increment = () => {
  state.count++
}

const decrement = () => {
  state.count--
}

const toggleTheme = () => {
  state.theme = state.theme === 'light' ? 'dark' : 'light'
  if (state.theme === 'dark') {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
}
</script>

<template>
  <div class="grid bg-gray-300 dark:bg-gray-700 center gap-1 p-4">
    <h1 class="text-center text-3xl dark:text-white">{{ state.count }}</h1>
    <div class="flex justify-center gap-2">
      <button class="btn-primary" @click="increment">+ Increment</button>
      <button class="btn-danger" @click="decrement">- Decrement</button>
    </div>
    <div class="flex justify-center mt-3">
      <button class="btn-theme-switcher" @click="toggleTheme">
        {{ state.theme === 'light' ? 'Dark' : 'Light' }}
      </button>
    </div>
  </div>
</template>
