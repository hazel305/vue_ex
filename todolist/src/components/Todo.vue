<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    toggleCheckbox(e) {
      this.$emit("toggle-checkbox", {
        id: this.todo.id,
        checked: e.target.checked,
      });
    },
    clickdelete() {
      this.$emit("click-delete", this.todo.id);
    },
  },
};
</script>

<template>
  <div>
    <div class="form-check" :data-id="todo.id">
      <input
        class="form-check-input"
        type="checkbox"
        value=""
        :id="'input' + todo.id"
        @change="toggleCheckbox"
      />
      <label
        class="form-check-label"
        :for="`input${todo.id}`"
        :style="todo.checked ? 'text-decoration:line-through' : ''"
      >
        {{ todo.text }}
      </label>
      <button
        type="button"
        class="btn btn-danger btn-sm mx-3"
        @click="clickdelete"
      >
        delete
      </button>
    </div>
  </div>
</template>

<style></style>
