<script setup>
import { ref } from "vue";
import TodoItem from "./TodoItem.vue";

const newTodoTitle = ref("");
const todoList = ref([
  {
    id: 1,
    title: "Learn Vuejs",
  },
  {
    id: 2,
    title: "Do an example",
  },
]);

function addNewTodo() {
  todoList.value.push({
    id: todoList.value.length + 1,
    title: newTodoTitle.value,
  });
  newTodoTitle.value = "";
}
</script>

<template>
  <form @submit.prevent="addNewTodo">
    <label>Add a todo</label>
    <input v-model="newTodoTitle" id="new-todo" placeholder="Example: Eating" />
    <button>Add</button>
  </form>
  <ul>
    <TodoItem
      v-for="(todo, index) in todoList"
      :key="todo.id"
      :title="todo.title"
      @delete="todoList.splice(index, 1)"
    ></TodoItem>
  </ul>
</template>
