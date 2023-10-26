<script>
export default {
  mounted() {
    this.$refs.username.focus();
    console.log(this.$refs.items);
    //document.querySelector("#username").focus();
  },
  data() {
    return {
      list: [
        { id: 1, title: "HTML", desc: "HTML ..." },
        { id: 2, title: "CSS", desc: "CSS ..." },
        { id: 3, title: "Javascript", desc: "Javascript ..." },
      ],
    };
  },
};
</script>

<template>
  <div class="layout">
    <h1>This is refs page</h1>

    <input ref="input" />
    <!-- <input type="text" id="username" /> -->

    <ul>
      <li v-for="item in list" ref="items" :key="item.id">
        {{ item.title }}
      </li>
    </ul>
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
</style>
