<template>
  <div class="container">
    <h1>오늘의 할일</h1>
    <TodoBasicForm @add-todo="onAdd" />
    <TodoList :todos="todos" @toggle-todo="toggleTodo"/>
    <div v-if="!todos.length">등록된 일정이 없습니다.</div>
  </div>
</template>

<script>
import { ref } from "vue";
import TodoBasicForm from "./components/TodoBasicForm.vue";
import TodoList from "./components/TodoList.vue";
export default {
  components: { TodoBasicForm, TodoList },
  setup() {
    let todos = ref([]);
    const todoStyle = {
      color: "gray",
      textDecoration: "line-through",
    };
    const deleteTodo = (data) => {
      todos.value.splice(data, 1);
    };
    const toggleTodo=(index)=>{
     console.log("eeee",todos[index]);
      //todos.value[index].completed=!todos.value[index].completed

    }
    const onAdd = (todo) => {
      todos.value.push(todo);
    };

    return {
      toggleTodo,
      onAdd,
      deleteTodo,
      todoStyle,
      todos,
    };
  },
};
</script>

<style>
.red {
  color: red;
}
.todo {
  color: gray;
  text-decoration: line-through;
}
</style>