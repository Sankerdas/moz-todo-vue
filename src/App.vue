<template>
  <div id="app">
    <h1>TODO LIST</h1>
    <ToDoForm @todo-added="addToDo" />
    <ul>
      <li v-for="todo in ToDoItems" :key="todo.id" >
        <ToDoItem :label="todo.label" :done="todo.done" :id="todo.id" />
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem';
import ToDoForm from './components/ToDoForm';

import uniqueId from 'lodash.uniqueid';

export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm
  },
  data() {
    return {
      ToDoItems: [
        {id: uniqueId("todo-") ,  label: "Set up basic vue app", done: true},
        {id: uniqueId("todo-") ,  label: "Learned about props and state", done: true},
        {id: uniqueId("todo-") ,  label: "Vue life cycle", done: false}
      ]
    }
  },
  methods: {
    addToDo(todoLabel) {
      console.log("add", todoLabel);
      this.ToDoItems.push(
        {id: uniqueId('todo-'), label: todoLabel, done: false }
      );
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
