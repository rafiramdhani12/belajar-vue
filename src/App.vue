<script setup>
import FormTodo from "./components/FormTodo.vue";
import { ref, onMounted } from "vue";
import TodoList from "./components/TodoList.vue";

// isi tipe data ref bisa tipe data apa saja
// jika seperti ini sudah menjadi state
const todos = ref([]);

onMounted(() => {
  const data = JSON.parse(localStorage.getItem("todos"));
  if (data) {
    todos.value = data;
  }
});

function add(data) {
  todos.value.push({ id: crypto.randomUUID(), todo: data.todo });
  save();
  data.clear();
}
function remove(id) {
  todos.value = todos.value.filter((item) => item.id !== id);
  save();
}

function save() {
  localStorage.setItem("todos", JSON.stringify(todos.value));
}
</script>

<template>
  <section class="wrapper">
    <FormTodo @addTodo="add" />
    <TodoList :todos="todos" @remove="remove" />
  </section>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  height: 100svh;
  justify-content: center;
  align-items: center;
}
</style>
