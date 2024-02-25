<template>
    <div>
      <input v-model="text" @keyup.enter="addTodo" placeholder="Enter your todo" />
      <button @click="addTodo">Add</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        text: '',
      };
    },
    methods: {
      addTodo() {
        if (this.text.trim() !== '') {
          this.$emit('addTodo', this.text);
          this.text = '';
        }
      },
    },
  };
  </script>