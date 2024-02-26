<template>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      <input type="checkbox" :checked="todo.completed" @change="toggleComplete(index)" />
      <span>{{ todo.text }}</span>
      <button @click="deleteTodo(index)">Delete</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['todos', 'deleteTodo', 'toggleComplete']
};
</script>
