<template>
  <div>
    <header>
      <button @click="filter = 'all'">All</button>
      <button @click="filter = 'active'">Active</button>
      <button @click="filter = 'completed'">Completed</button>
    </header>
    <todo-input @addTodo="addTodo" />
    <todo-list :todos="filteredTodos" @deleteTodo="deleteTodo" />
    <todo-footer :todos="todos" />
  </div>
</template>

<script >
import { ref, reactive, computed } from 'vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  components: {
    TodoInput,
    TodoList,
    TodoFooter,
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

    const filteredTodos = reactive(
      computed(() => {
        if (filter.value === 'all') return todos.value;
        return todos.value.filter(todo => filter.value === 'active' ? !todo.completed : todo.completed);
      })
    );

    return { todos, filter, addTodo, deleteTodo, filteredTodos };
  },
};
</script>