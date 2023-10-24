<script>
export default {
  data() {
    return {
      isActive: true,
      error: null,
      activeClass: "active",
      errorClass: "text-danger",
    };
  },
  computed: {
    classObject() {
      return {
        active: this.isActive && !this.error,
        "text-danger": this.error && this.error.type === "fatal",
      };
    },
  },
};
</script>

<template>
  <div class="about">
    <h1>Class style Binding page</h1>
    <div class="normal" :class="classObject"></div>
    <div :class="[activeClass, errorClass]"></div>
    <div :class="[isActive ? activeClass : '', errorClass]"></div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
45 changes: 45 additions & 0 deletions45 src/views/ComputedView.vue
