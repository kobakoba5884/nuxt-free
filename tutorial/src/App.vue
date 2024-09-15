<script setup>
import { reactive, ref } from 'vue'

const counter = reactive({
  count: 0
})

counter.count++

const message = ref('Hello World!')

message.value = 'Changed the message !'

</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is {{ counter.count }}</p>
  <h1>{{ message.split(' ').reverse().join(' ') }}</h1>
</template>