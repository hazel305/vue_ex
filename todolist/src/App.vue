<script>
export default {
  data() {
    return {
      todoText: "",
      todos: [
        { id: 1, text: "learn chapter1", checked: false },
        { id: 2, text: "learn chapter2", checked: false },
        { id: 3, text: "learn chapter3", checked: false },
      ],
    };
  },
};
</script>

<template>
  <div class="container">
    <h1 class="text-center">todo App</h1>
    <div class="mb-3">
      <label for="todo" class="form-label">Todo Input</label>
      <input
        type="text"
        class="form-control"
        id="todo"
        placeholder="Add todo"
      />
    </div>
  </div>
</template>

<style scoped></style>
