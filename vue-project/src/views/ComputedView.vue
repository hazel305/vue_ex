<script setup>
import { reactive, computed } from "vue";

const author = reactive({
  name: "John Doe",
  books: [
    "Vue 2 - Advanced Guide",
    "Vue 3 - Basic Guide",
    "Vue 4 - The Mystery",
  ],
  firstName: "John",
  lastName: "Doe",
});

const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? "Yes" : "No";
});

const fullName = computed({
  get() {
    return author.firstName + " " + author.lastName;
  },
  set(newValue) {
    const [first, last] = newValue.split(" ");
    author.firstName = first;
    author.lastName = last;
  },
});
</script>

<template>
  <div class="layout">
    <h1>This is a computed properties page</h1>

    <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span>

    <hr />
    <div>Name: {{ fullName }}</div>
    <div>Name: {{ (fullName = "길동 홍") }}</div>
    <div>Name: {{ (fullName = " 김") }}</div>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .layout {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
