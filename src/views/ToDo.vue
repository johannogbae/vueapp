<template>
    <div class="myDiv">
      <h1>My To-do List</h1>
      <input type="text" v-model="todolist" @keyup.enter="addItem">
      <button @click="addItem">Add Item</button>
      <ul v-if="task.length > 0">
        <li v-for="(item, index) in task" :key="index">
          {{ index + 1 }}. {{ item }}
          <button @click="removeItem(index)">Remove</button>
        </li>
      </ul>
      <p v-else>Yeah! all tasks are complete.</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const itemID = ref(0)
  const todolist = ref('')
  const task = ref([])
  const shopped = ref(false)
  
  const addItem = () => {
    if (todolist.value.trim() !== '') {
      task.value.push(todolist.value)
      todolist.value = ''
    }
  }
  
  const removeItem = (index) => {
    task.value.splice(index, 1)
  }
  </script>
  
  <style scoped>
  .myDiv {
    border: 5px outset aquamarine;
    background-color: rgb(232, 238, 240);
    text-align: center;
    padding: 60px;
  }
  
  button {
    margin-left: 10px;
  }
  </style>
  