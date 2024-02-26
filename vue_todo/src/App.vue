<template>
  <div class="container">
    <header>
      <button @click="changeFilter('all')">All</button>
      <button @click="changeFilter('active')">Active</button>
      <button @click="changeFilter('completed')">Completed</button>
    </header>
    <TodoInput :addTodo="addTodo" />
    <TodoList :todos="filteredTodos" :deleteTodo="deleteTodo" :toggleComplete="toggleComplete" />
    <TodoFooter :todos="todos" />
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  components: {
    TodoInput,
    TodoList,
    TodoFooter
  },
  setup() {
    const todos = ref([]);
    const filter = ref('all');

    const addTodo = text => {
      todos.value.push({ text, completed: false });
    };

    const deleteTodo = index => {
      todos.value.splice(index, 1);
    };

    const toggleComplete = index => {
      todos.value[index].completed = !todos.value[index].completed;
    };

    const changeFilter = filterValue => {
      filter.value = filterValue;
    };

    const filteredTodos = computed(() => {
      if (filter.value === 'all') return todos.value;
      return todos.value.filter(todo => (filter.value === 'active' ? !todo.completed : todo.completed));
    });

    return {
      todos,
      filter,
      addTodo,
      deleteTodo,
      toggleComplete,
      changeFilter,
      filteredTodos
    };
  }
};
</script>
