<template>
    <div>
      <span>{{ activeCount }} items left</span>
      <button @click="clearCompleted">Clear completed</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      todos: Array,
    },
    computed: {
      activeCount() {
        return this.todos.filter(todo => !todo.completed).length;
      },
    },
    methods: {
      clearCompleted() {
        this.$emit('clearCompleted');
      },
    },
  };
  </script>