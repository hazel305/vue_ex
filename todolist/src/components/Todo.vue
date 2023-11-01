<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isEditing: false, // 수정 모드 여부
      editedText: this.todo.text, // 수정한걸 저장
    };
  },
  methods: {
    toggleCheckbox(e) {
      this.$emit("toggle-checkbox", {
        id: this.todo.id,
        checked: e.target.checked,
      });
    },
    clickDelete() {
      this.$emit("click-delete", this.todo.id);
    },
    startModify() {
      this.isEditing = true;
    },
    finishModify() {
      this.isEditing = false;
      this.$emit("click-modify", this.todo.id, this.editedText);
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
        :style="todo.checked ? 'text-decoration: line-through' : ''"
      >
        <input
          v-if="isEditing"
          class="form-control"
          v-model="editedText"
          @keyup.enter="finishModify"
        />
        <span v-else>{{ todo.text }}</span>
      </label>
      <button type="button" class="btn btn-sm btn-light modify-btn" @click="startModify">
        Modify
      </button>
      <button
        v-if="!isEditing"
        type="button"
        class="btn btn-danger btn-sm mx-3"
        @click="clickDelete"
      >
        Delete
      </button>
      <button
        v-if="isEditing"
        type="button"
        class="btn btn-primary btn-sm mx-2"
        @click="finishModify"
      >
        Done
      </button>
    </div>
  </div>
</template>

<style></style>
