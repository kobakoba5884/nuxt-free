<script setup>
import { ref } from 'vue';

const titleValue = 'title'
const titleClass = ref(titleValue)
const changeColor = () => {
  titleClass.value = titleClass.value === titleValue ? '' : titleValue
}
</script>

<template>
  <h1 :class="titleClass">Make me red!</h1>
  <button @click="changeColor">smash</button>
</template>

<style>
.title {
  color: red;
}
</style>