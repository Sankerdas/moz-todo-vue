<template>
  <div id="app">
    <h1>TODO LIST</h1>
    <ul>
      <li v-for="todo in ToDoItems" :key="todo.id" >
        <ToDOItem :label="todo.label" :done="true" />
      </li>
    </ul>
  </div>
</template>

<script>
import ToDOItem from './components/ToDoItem';
import uniqueId from 'lodash.uniqueid';

export default {
  name: 'App',
  components: {
    ToDOItem
  },
  data() {
    return {
      ToDoItems: [
        {id: uniqueId("todo-") ,  label: "Set up basic vue app", done: true},
        {id: uniqueId("todo-") ,  label: "Learned about props and state", done: true},
        {id: uniqueId("todo-") ,  label: "Vue life cycle", done: false}
      ]
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
