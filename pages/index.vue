<template>
  <div>
    <h1>Todo list</h1>
    <div>
      <input v-model="newTodo.name" type="text"> <button @click="addTodo">dodaj</button>
    </div>
    <div v-for="(todo, index) in todos" :key="index">
      <input v-model="todo.done" type="checkbox"> {{todo.name}} <button @click="removeTodo(index)">usuń</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Todo from "../models/Todo";

@Component
export default class Index extends Vue {
  todos: Array<Todo> = [];

  newTodo: Todo = {
    name: '',
    done: false
  };
  
  addTodo () {
    this.todos.push(this.newTodo);

    this.newTodo = {
      name: '',
      done: false
    };
  }

  removeTodo (index) {
    this.todos.splice(index, 1);
  }
}
</script>

<style>

</style>
