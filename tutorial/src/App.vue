<script setup>
import { ref } from 'vue'

const inputValue = ref('')
const onInput = (e) => {
  inputValue.value = e.target.value
}
const textAreaValue = ref('')

const inputModel = defineModel('inputModel')
const messageModel = defineModel('messageModel')
</script>

<template>
  <input type="text" @input="onInput" placeholder="Type here." />
  <p>{{ inputValue }}</p>
  <textarea @input="(e) => (textAreaValue = e.target.value)"></textarea>
  <p>{{ textAreaValue }}</p>
  <input v-model="inputModel" />
  <p>{{ inputModel }}</p>
  <p>Message is: {{ messageModel }}</p>
  <input v-model="messageModel" placeholder="edit me" />
</template>
