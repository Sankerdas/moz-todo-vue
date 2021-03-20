<template>
  <div id="app">
    <h1>TODO LIST</h1>
    <ul>
      <li>
        <ToDOItem label="hello" :done="true" />
      </li>
    </ul>
  </div>
</template>

<script>
import ToDOItem from './components/ToDoItem';

export default {
  name: 'App',
  components: {
    ToDOItem
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
