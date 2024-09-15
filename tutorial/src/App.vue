<script setup>
import { ref, computed } from 'vue';

let id = 0
const hideCompleted = ref(false)
const inputModel = defineModel('inputModel')
const todos = ref([
  { id: id++, text: 'Learn HTML' , done: true},
  { id: id++, text: 'Learn JavaScript' , done: true},
  { id: id++, text: 'Learn Vue' , done: false}
])

const addTodo = () => {
  todos.value.push({
    id: id++, text: inputModel.value
  })
}

const removeTodo = (todo) => {
  todos.value = todos.value.filter(t => t.id !== todo.id)
}

const filteredTodos  = computed(() => {
  return hideCompleted.value ? todos.value.filter(t => !t.done) : todos.value
})

</script>

<template>
  <div>
    <input placeholder="new todo" v-model="inputModel" required>
    <button @click="addTodo">Add Todo</button>
  </div>
  <hr>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">{{ hideCompleted ? 'Show all' : 'Hide completed' }}</button>
</template>

<style>
.done{
  text-decoration: line-through;
}
</style>