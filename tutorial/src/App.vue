<script setup>
import { ref } from 'vue';

let id = 0
const inputModel = defineModel('inputModel')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

const addNewTodo = () => {
  todos.value.push({
    id: id++, text: inputModel.value
  })
}

const removeTodo = (todo) => {
  todos.value = todos.value.filter(t => t.id !== todo.id)
}

</script>

<template>
  <div>
    <input placeholder="new todo" v-model="inputModel">
    <button @click="addNewTodo">Add Todo</button>
  </div>
  <hr>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <span>{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>