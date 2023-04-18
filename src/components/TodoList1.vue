<template>
  <div class="card">
    <div class="card-body p-2">
      <div class="d-flex" v-for="i in todos" :key="i.id">
        <div class="form-check flex-grow-1">
          <label class="form-check-label">
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
          <button class="btn btn-danger btn-sm" @click="deleteTodo(i)">
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
  emits: ["toggle-todo"],
  setup(props, { emit }) {
    const toggleTodo = (index) => {
      console.log(index);
      emit("toggle-todo", index);
    };
    return {
      toggleTodo,
    };
  },
};
</script>

<style>
</style>