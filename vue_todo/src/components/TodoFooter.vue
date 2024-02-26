<template>
  <div>
    <p>총 {{ total }}개의 할일 중 {{ completed }}개 완료</p>
  </div>
</template>

<script>
import { computed } from 'vue';

export default {
  props: ['todos'],
  setup(props) {
    const total = computed(() => props.todos.length);
    const completed = computed(() => props.todos.filter(todo => todo.completed).length);

    return {
      total,
      completed
    };
  }
};
</script>
