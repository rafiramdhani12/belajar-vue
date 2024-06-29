<script setup>
import { ref } from "vue";

const todo = ref("");

function clear() {
  todo.value = "";
}
</script>

<template>
  <form @:submit.prevent="$emit('addTodo', { todo, clear })">
    <h1 class="title">todo</h1>
    <div class="form-control">
      <label for="todo">Todo :</label>
      <!-- cara kerja vmodel adalah bind value dan berikan event pada inputan -->
      <input
        type="text"
        v-model="todo"
        id="todo"
        placeholder="Your todo"
        required
      />
    </div>
    <div style="text-align: end">
      <button>Add</button>
    </div>
  </form>
</template>

<style scoped>
form {
  margin-bottom: 1rem;
}

.title {
  font-size: 1.5rem;
  text-align: center;
  margin-bottom: 2rem;
}

.form-control {
  margin-bottom: 1rem;
}

.form-control label {
  margin-right: 1rem;
}
</style>
