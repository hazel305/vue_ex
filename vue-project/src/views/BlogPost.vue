<script>
export default {
  props: ["title"],
  emits: ["enlarge-text", "smaller-text"],
};
</script>

<template>
  <div>{{ title }}</div>
  <button @click="$emit('enlarge-text')">텍스트 확대</button>
  <button @click="$emit('smaller-text')">텍스트 축소</button>
</template>

<style>
@media (min-width: 1024px) {
  .layout {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
