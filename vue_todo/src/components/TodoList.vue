<template>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.completed" />
        <span>{{ todo.text }}</span>
        <button @click="deleteTodo(index)">Delete</button>
      </li>
    </ul>
  </template>
  
  <script>
  export default {
    props: {
      todos: Array,
    },
    methods: {
      deleteTodo(index) {
        this.todos.splice(index, 1); // 배열에서 요소 삭제
      },
    },
  };
  </script>