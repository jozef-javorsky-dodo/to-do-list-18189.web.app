<template>

  <div class="container mx-auto p-4 bg-amber-100">

    <h1 class="text-3xl font-bold mb-4"> 📝 To~Do~List 📒 </h1>

    <div class="flex mb-4">

      <input type="text" v-model="newTodoText" @keyup.enter="addTodo" placeholder="Add a new to-do note."
        class="border border-gray-400 rounded px-3 py-2 flex-grow mr-2">

      <button @click="addTodo" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
        Add
      </button>

    </div>

    <ul>

      <li v-for="(todo, index) in todos" :key="index" class="flex items-center mb-2">

        <input type="checkbox" v-model="todo.completed" class="mr-2">

        <span :class="{ 'line-through': todo.completed }">{{ todo.text }}</span>

        <button @click="removeTodo(index)" class="ml-auto text-red-500 hover:text-red-700">
          Remove
        </button>

      </li>

    </ul>

    <div class="mt-4">

      <br>

      <hr>

      <p>
        <a href="mailto:jozef.javorsky.dodo@gmail.com">jozef.javorsky.dodo@gmail.com</a>
      </p>

      <br>

      <p>
        <a href="https://github.com/jozef-javorsky-dodo" target="_blank">GitHub: jozef-javorsky-dodo</a>
      </p>

    </div>

  </div>

</template>

<script setup>

import { ref } from 'vue';

const newTodoText = ref('');

const todos = ref([]);

const addTodo = () => {
  if (newTodoText.value.trim() !== '') {
    todos.value.push({ text: newTodoText.value, completed: false });
    newTodoText.value = '';
  }
};


const removeTodo = (index) => {
  todos.value.splice(index, 1);
};

definePageMeta({
  title: '📝 To~Do~List 📒',
  charset: 'UTF-8',
  viewport: 'width=device-width, initial-scale=1.0',
  description: 'Nuxt Vue stuff.',
  author: 'jozef.javorsky.dodo@gmail.com, github.com/jozef-javorsky-dodo'
});

onMounted(() => {
  document.body.style.backgroundColor = "rgb(122, 122, 122)";
});

</script>