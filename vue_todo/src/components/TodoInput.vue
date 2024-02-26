<template>
  <form @submit.prevent="handleSubmit">
    <input type="text" placeholder="Enter a todo..." v-model="text" />
    <button type="submit">Add</button>
  </form>
</template>

<script>
import { ref } from 'vue';

export default {
  props: ['addTodo'],
  setup(props) {
    const text = ref('');

    const handleSubmit = () => {
      if (!text.value.trim()) return;
      props.addTodo(text.value);
      text.value = '';
    };

    return {
      text,
      handleSubmit
    };
  }
};
</script>
