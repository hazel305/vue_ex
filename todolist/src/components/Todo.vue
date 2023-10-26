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
      <label class="form-check-label" :for="`input${todo.id}`">
        {{ todo.text }}
      </label>
    </div>
  </div>
</template>

<style></style>
