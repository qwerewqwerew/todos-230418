<template>
  <div class="card">
    <div class="card-body p-2">
      <div class="d-flex" v-for="(i, index) in todos" :key="i.id">
        <div class="form-check flex-grow-1">
          <label class="form-check-label" :class="{ todo: i.completed }">
            {{ i.subject }}
            <input
              type="checkbox"
              class="form-check-input"
              :value="todos.completed"
              @change="toggleTodo(index)"
            />
          </label>
        </div>
        <div>
          <button class="btn btn-danger btn-sm" @click="deleteTodo(index)">
            삭제
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  emits: ["toggle-todo", "delete-todo"],
  setup(props, { emit }) {
    const toggleTodo = (index) => {
      emit("toggle-todo", index);
    };
    const deleteTodo = (index) => {
      emit("delete-todo", index);
    };
    return {
      toggleTodo,
      deleteTodo,
    };
  },
};
</script>

<style></style>
