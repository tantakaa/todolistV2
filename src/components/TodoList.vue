<template>
  <div class="title">TodoList</div>
  <div v-for="todo in todos" :key="todo.name">
    <div class="todo">
      <span class="name">Todo: {{ todo.name }}, </span>
      <span class="state" v-if="todo.state == 0">State: Not Yet </span>
      <span class="state" v-if="todo.state != 0">State: Done </span>
      <button @click="todo.state += 1" v-if="todo.state == 0">done</button>
    </div>
  </div>
  <div>
    <label>
      Todo
      <input v-model="newTodoName" type="text" />
    </label>
    <button @click="addTodo">add</button>
  </div>

  <div class="title">Done</div>
  <div v-for="todo in todos" :key="todo.name">
    <div class="todo" v-if="todo.state != 0">
      <span class="name">Todo: {{ todo.name }}, </span>
      <span class="state">State: Done </span>
    </div>
  </div>

  <div class="title">Not Yet</div>
  <div v-for="todo in todos" :key="todo.name">
    <div class="todo" v-if="todo.state == 0">
      <span class="name">Todo: {{ todo.name }}, </span>
      <span class="state">State: Not Yet </span>
      <button @click="todo.state += 1">done</button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "TodoList",
  setup() {
      const todos = ref([]);
      const newTodoName = ref("");
      const addTodo = () => {
          todos.value.push({ name: newTodoName.value, state: 0 });
      };
      return { todos, newTodoName, addTodo };
  }
};
</script>

<style>
.title {
  font-size: 18pt;
  padding: 1em;
}
</style>