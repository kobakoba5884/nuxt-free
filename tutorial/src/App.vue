<script setup>
import ChildComp from './components/ChildComp.vue'

const inputModel = defineModel()

</script>

<template>
  <ChildComp :msg="inputModel"/>
  <input v-model="inputModel">
</template>