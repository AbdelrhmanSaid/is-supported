<script setup>
import { computed, ref } from 'vue'

const prop = ref('display: grid')
const supported = computed(() => window.CSS.supports(prop.value))
</script>

<template>
  <main>
    <h1>Does this work on my browser?</h1>
    <label :class="{ supported }">
      <input type="text" v-model="prop" placeholder="Enter a CSS property..." />
    </label>
  </main>
</template>

<style>
@import './base.css';

main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  height: 100vh;
}

h1,
input {
  color: #121212;
}

label {
  position: relative;
  width: 100%;
}

input {
  width: 100%;
  padding: 1rem;
  font-size: 1.2rem;
  border-radius: 0.25rem;
  background-color: #e5e5e5;
  border: 1px solid transparent;
}

input:focus {
  outline: none;
}

label::after {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  font-size: 1.5rem;
}

label.supported input {
  border: 1px solid #74d46c
}

label:not(.supported) input {
  border: 1px solid #d46c6c;
}

label.supported::after {
  content: '✅';
}

label:not(.supported)::after {
  content: '⚠️';
}
</style>
