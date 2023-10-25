<script>
// const awesome = true;

export default {
  data() {
    return {
      awesome: true,
      type: "C",
      page: true,
    };
  },
};
</script>

<template>
  <div class="layout">
    <h1>This is conditional Rendering page</h1>
    <button @click="awesome = !awesome">Toggle</button>

    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>
    {{ awesome }}
    <hr />
    <div v-if="type === 'A'">A</div>
    <div v-else-if="type === 'B'">B</div>
    <div v-else-if="type === 'C'">C</div>
    <div v-else>A/B/C 아님</div>

    <hr />
    <button @click="page = !page" :class="{ active: page }">페이지 전환</button>
    <template v-if="page">
      <h1>제목</h1>
      <p>단락 1</p>
      <p>단락 2</p>
      <div v-show="true">Hello!</div>
    </template>
    <template v-else>
      <h1>제목 2</h1>
      <p>단락 1</p>
      <p>단락 2</p>
      <div v-show="true">World!</div>
    </template>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .layout {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

button.active {
  background: #000;
  color: #fff;
}
</style>
